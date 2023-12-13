class Movies {
  constructor() {
    this.movies = [];
  }

  getAllMovies() {
    return this.movies;
  }

  addMovie(title, director, year, genre) {
    if (!title || !director || !year || !genre) return undefined;

    const isExist = this.movies.find((element) => {
      if (
        element.title.toLowerCase() === title.toLowerCase() &&
        element.director.toLowerCase() === director.toLowerCase()
      ) {
        return true;
      }

      return false;
    });

    if (isExist) return undefined;

    const movieNew = {
      title: title,
      director: director,
      year: year,
      genre: genre,
    };

    this.movies.push(movieNew);

    return movieNew;
  }

  updateMovie(title, updatedDetails) {
    const isExist = this.movies.find((element) => {
      if (element.title.toLowerCase() === title.toLowerCase()) {
        return true;
      }

      return false;
    });

    if (!isExist) return undefined;

    if (updatedDetails.director) {
      isExist.director = updatedDetails.director;
    }

    if (updatedDetails.year) {
      isExist.year = updatedDetails.year;
    }

    if (updatedDetails.genre) {
      isExist.genre = updatedDetails.genre;
    }

    return isExist;
  }

  deleteMovieByTitle(title) {
    const filterd = this.movies.filter(
      (element) => element.title.toLowerCase() != title.toLowerCase(),
    );
    this.movies = filterd;
  }
}

module.exports = Movies;
