import java.util.ArrayList;
import java.util.HashMap;
import java.util.List;
import java.util.Map;

class Movie {
    String title;
    String ratingCategory;
    double ratingScore;

    public Movie(String title, String ratingCategory, double ratingScore) {
        this.title = title;
        this.ratingCategory = ratingCategory;
        this.ratingScore = ratingScore;
    }
}

public class MovieRatings {
    public static void main(String[] args) {
        List<Movie> movies = new ArrayList<>();
        movies.add(new Movie("Movie A", "PG", 7.5));
        movies.add(new Movie("Movie B", "PG-13", 8.0));
        movies.add(new Movie("Movie C", "R", 9.0));
        movies.add(new Movie("Movie D", "PG", 6.5));
        movies.add(new Movie("Movie E", "PG-13", 7.0));
        movies.add(new Movie("Movie F", "R", 8.5));

        Map<String, List<Double>> ratingsMap = new HashMap<>();

        for (Movie movie : movies) {
            ratingsMap.putIfAbsent(movie.ratingCategory, new ArrayList<>());
            ratingsMap.get(movie.ratingCategory).add(movie.ratingScore);
        }

        for (Map.Entry<String, List<Double>> entry : ratingsMap.entrySet()) {
            String category = entry.getKey();
            List<Double> scores = entry.getValue();
            double totalScore = 0;
            for (Double score : scores) {
                totalScore += score;
            }
            double averageScore = totalScore / scores.size();
            System.out.println("Category: " + category + ", Number of movies: " + scores.size() + ", Average rating: " + averageScore);
        }
    }
}