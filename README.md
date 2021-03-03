# Identicon

An identicon is a visual representation of a hash value. A familiar example is a default image generated for a GitHub user. An identicon contains a 5x5 grid of squares, each 50px tall and 50px wide. Some of the squares are colorized, and the pattern is "mirrored" on the left and right sides of the image, split by a vertical axis down the middle.

## How It Works


A string input from the user is hashed and converted into a series of 16 numbers.
```elixir
[114, 179, 2, 191, 41, 122, 34, 138, 117, 115, 1, 35, 239, 239, 124, 65]
```
Each 50x50px square in the image is assigned an "index", following the mirror pattern described above. For example:

```
 _____________________________
|     |     |     |     |     |
|  A  |  B  |  C  |  B  |  A  |
|_____|_____|_____|_____|_____|
|     |     |     |     |     |
|  D  |  E  |  F  |  E  |  D  |
|_____|_____|_____|_____|_____|
|     |     |     |     |     |
|  G  |  H  |  I  |  H  |  G  |
|_____|_____|_____|_____|_____|
|     |     |     |     |     |
|  J  |  K  |  L  |  K  |  J  |
|_____|_____|_____|_____|_____|
|     |     |     |     |     |
|  M  |  N  |  O  |  N  |  M  |
|_____|_____|_____|_____|_____|

```
15 of the 16 numbers are applied to the indices of the grid, based on the index of each number the list (e.g. A = 114, B = 179, etc.). Squares are colored if the number applied is even. The color chosen is an RGB value derived from the first three numbers in the list.

Example:
```elixir
iex> Identicon.main("brendan")
```

![brendan.png](./brendan.png)