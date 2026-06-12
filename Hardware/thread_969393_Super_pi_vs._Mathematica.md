---
title: "Super pi vs. Mathematica"
date: 2008-11-03
forum: Hardware
---

### Post by Paul Miller on 2008-11-03
Just out of curiosity, I downloaded the Linux version of super pi to see how my CPU measured up.  Doing
```

./super_pi 20

```
to calculate 1048576 decimal digits of pi took approximately 43.5 seconds.  However, the same calculation (writing the output to PI.DAT just like super pi does) using the following line of *Mathematica* code
```

Timing [Export ["PI.DAT", N[Pi, 1048576]];]

```
took 11.8 seconds.  

My question is: why the big discrepency?

---

