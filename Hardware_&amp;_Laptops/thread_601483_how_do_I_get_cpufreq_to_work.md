---
title: "how do I get cpufreq to work?"
date: 2007-11-03
forum: Hardware &amp; Laptops
---

### Post by riddlebox on 2007-11-03
I used to be able to select what freq I wanted my cpu to be running at, at that moment, and if I needed more it would bump up on its own, and even go down on its own, after I upgraded to gutsy my cpu is always running at the most?

---

### Post by komputes on 2008-02-21
cpufreq-utils contains 2 utilities:

cpufreq-set - lets you set the frequency of the CPU through the command line
cpufreq-info - lets you view info on you CPU and possible modes (governors)

For a manual/instructions type the following in a console:

```
man cpufreq-set
```

---

