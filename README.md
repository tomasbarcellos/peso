
<!-- README.md is generated from README.Rmd. Please edit that file -->

# peso

<!-- badges: start -->

<!-- badges: end -->

Carregando pacotes

Criando gráfico com o peso

``` r
peso <- readr::read_csv2("peso.csv", col_types = "cd") %>% 
  mutate(data = lubridate::dmy(data))
#> ℹ Using "','" as decimal and "'.'" as grouping mark. Use `read_delim()` for more control.

etiquetas <- peso %>% 
  filter(seq_along(data) %in% c(1, n()))

ggplot(peso, aes(data, peso)) +
  geom_point(col = "cornflowerblue", size = 2) +
  geom_line(linetype = "dashed") +
  geom_text(aes(label = peso), etiquetas, nudge_y = 0.5)
#> Warning: Removed 7 rows containing missing values (geom_point).
```

![](README_files/figure-gfm/unnamed-chunk-3-1.png)<!-- -->
