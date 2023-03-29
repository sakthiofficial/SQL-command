CREATE DATABASE imdb;

USE imdb;

CREATE TABLE Movie (
  movie_id INT AUTO_INCREMENT PRIMARY KEY,
  title VARCHAR(255),
  release_year INT,
  description TEXT,
  runtime INT,
  rating DECIMAL(3,1)
);

CREATE TABLE Media (
  media_id INT AUTO_INCREMENT PRIMARY KEY,
  movie_id INT,
  type ENUM('Video', 'Image'),
  url VARCHAR(255),
  FOREIGN KEY (movie_id) REFERENCES Movie(movie_id)
);

CREATE TABLE Genre (
  genre_id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(255)
);

CREATE TABLE Review (
  review_id INT AUTO_INCREMENT PRIMARY KEY,
  movie_id INT,
  user_id INT,
  rating INT,
  comment TEXT,
  FOREIGN KEY (movie_id) REFERENCES Movie(movie_id),
  FOREIGN KEY (user_id) REFERENCES User(user_id)
);

CREATE TABLE User (
  user_id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(255),
  email VARCHAR(255),
  password VARCHAR(255)
);

CREATE TABLE Artist (
  artist_id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(255)
);

CREATE TABLE Skill (
  skill_id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(255)
);

CREATE TABLE Role (
  role_id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(255)
);

CREATE TABLE Movie_Genre (
  movie_id INT,
  genre_id INT,
  PRIMARY KEY (movie_id, genre_id),
  FOREIGN KEY (movie_id) REFERENCES Movie(movie_id),
  FOREIGN KEY (genre_id) REFERENCES Genre(genre_id)
);

CREATE TABLE Movie_Artist (
  movie_id INT,
  artist_id INT,
  role_id INT,
  PRIMARY KEY (movie_id, artist_id, role_id),
  FOREIGN KEY (movie_id) REFERENCES Movie(movie_id),
  FOREIGN KEY (artist_id) REFERENCES Artist(artist_id),
  FOREIGN KEY (role_id) REFERENCES Role(role_id)
);

CREATE TABLE Artist_Skill (
  artist_id INT,
  skill_id INT,
  PRIMARY KEY (artist_id, skill_id),
  FOREIGN KEY (artist_id) REFERENCES Artist(artist_id),
  FOREIGN KEY (skill_id) REFERENCES Skill(skill_id)
);

CREATE TABLE Movie_Review (
  movie_id INT,
  review_id INT,
  PRIMARY KEY (movie_id, review_id),
  FOREIGN KEY (movie_id) REFERENCES Movie(movie_id),
  FOREIGN KEY (review_id) REFERENCES Review(review_id)
);



<img width="960" alt="2023-03-29" src="https://user-images.githubusercontent.com/112932102/228507027-64f089d1-7ff6-4c36-8e62-42edd8a89bc4.png">





