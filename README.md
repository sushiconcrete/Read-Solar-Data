# Read-Solar-Data
Using R to read solar data.
My workflow for this project can be divided into the following steps:\

1.  Focus on the first zip file to look for the pattern within it.
    -   Read wea and pvsyst file since their simplicity.

        -   Assuming each wea and pvsyst has same skip lines. Turns out they do.

    -   Read Stat file

        -   Resolved Difficulty:

            -   Encoding issue solved by explicitly claim that locale = locale(encoding = "ISO-8859-1")

            -   Choosing the end pattern: changing "[C]" to "-" since the pattern is that each information is fully displayed right after the next "-"

            -   Convert the column Day:Hour into time variables using the combination of paste0 and as.POSIXct. And it's important to match the final string with the format.

            -   In my convert to numeric function, it's important to convert only char into double instead of posixct, otherwise the posixct elements will end up with wrong values.
2.  Apply functions to the rest files
    -   When applying functions, I notice that it's worthy to add a if condition that recognizes the input value is the one we want to manipulate. Otherwise it will potentially change the data.
