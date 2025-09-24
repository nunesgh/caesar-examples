# Caesar Examples

## Lossy List

As per [Caesar's Guide to HeyVL](https://www.caesarverifier.org/docs/getting-started/heyvl-guide\#full-example).

## Probabilistic Choice

```
$x = -y\ {_{p}}{\oplus}\ x = +y$
```

## Approximate Probabilistic Counting

Abstract counting.

```
$\{ N + 1 \}$

VAR $k, n = 1, 0$
WHILE $n != N$:
    $k = 2k\ {_{\frac{1}{2}}}{\oplus}\ \text{SKIP}$
    $n = n + 1$

$\{ k \}$
```

Concrete counting.

```
$\{ N + 1 \}$

VAR $c, n = 0, 0$
WHILE $n != N$:
    $c = c + 1\ {_{(\frac{1}{2})^c}}{\oplus}\ \text{SKIP}$
    $n = n + 1$

$\{ 2^c \}$
```

## Unbiasing

Unbiased coin flip from biased coin flips.

```
$\{ \frac{1}{2} \}$

VAR $x, y = 0, 0$
WHILE $x == y$:
    $x = 0\ {_{p}}{\oplus}\ 1$
    $y = 0\ {_{p}}{\oplus}\ 1$

$\{ [x == 0] \}$
```

Alternative version using non-deterministic (demonic) choice for $p$.

```
$\{ \frac{1}{2} \}$

VAR $x, y = 0, 0$
WHILE $x == y$:
    $p \in \{ \text{values} \}$
    $x = 0\ {_{p}}{\oplus}\ 1$
    $y = 0\ {_{p}}{\oplus}\ 1$

$\{ [x == 0] \}$
```

## Quantum Entanglement

Delivery model of two entangled qbits transformed as a random walk program.

```
${T'(c)}$

VAR $c = 2$
VAR $n, m = 0, 0$
WHILE $c == 2$:
    WHILE $c > 0$:
        IF $c == 2$:
            $c = 1\ @\ 2p(1-p), c = 0\ @\ p^2, \text{SKIP}\ @\ (1 - p)^2$
        IF $c == 1$:
            $c = 0\ {_{p}}{\oplus}\ \text{SKIP}$
        $n = n + 1$
    $c = 2\ {_{q}}{\oplus}\ \text{SKIP}$
    $m = m + 1$

$\{ n + m \}$
```
