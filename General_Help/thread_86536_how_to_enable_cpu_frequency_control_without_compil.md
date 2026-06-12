---
title: "how to enable cpu frequency control without compile a new kernel"
date: 2005-11-05
forum: General Help
---

### Post by syons on 2005-11-05
I'm using Compaq presario 2500 and its cpu is pentium 4 mobile.  Cpudyn and cpufreq(a component in e17)say the cpu frequency control isn't enabled, How can I check it and make it run in a convenient way? Thank you.:KS
BTW, does powernow conflict with cpufreq?

---

### Post by Plank117 on 2005-11-05
Just use powernowd:
```
sudo powernowd
```
I have an Averatec C3500 and I was also informed that frequency scaling was not enabled, it works perfectly on my machine. You might want to take a look at the manual page, as it's pretty customizable.
```
man powernowd
```

---

### Post by syons on 2005-11-10
thank you.(forgive me for being late.....)

---

