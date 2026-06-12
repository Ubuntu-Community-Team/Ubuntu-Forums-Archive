---
title: "Turbo boost not working"
date: 2011-10-10
forum: Hardware
---

### Post by halfpower on 2011-10-10
I have an first generation i5 CPU.  I'm able to set frequency scaling governors such as performance, ondemand, powersave, etc.  My CPU, however, never reaches any of the turbo frequencies. In looking at my system, I haven't seen anything related to turbo boost either.  Is there a way to enable turbo boost?

---

### Post by snafu006 on 2011-10-10
Read this [http://ubuntuforums.org/showthread.php?t=1321028&page=2](http://ubuntuforums.org/showthread.php?t=1321028&page=2) and try this [http://code.google.com/p/i7z/](http://code.google.com/p/i7z/)

---

### Post by torkins on 2011-10-10
I'm having a similar issue. My laptop has an i7 2620QM, and although i7z displays Turbo Boost as being enabled, when pegging the CPU, i7z never shows any CPU exceeding the natural frequency 2.2Ghz, even though it should be able to reach 3.4Ghz as it does under Windows.

I'm currently on 11.04, any idea of the limitation here?

---

### Post by notmyidea on 2011-12-08
Same problem here.

i7 2600k.  i7z software shows it clocks down properly to 1.6GHz but when stressed, only clocks up to 3.4GHz, it's natural frequency.  I have it overclocked to 4.6GHz and it works fine in windoze.  Xubuntu 11.10

---

### Post by xanadux on 2011-12-11
Same issue here with an i7-2760QM in a system76 laptop. At full load (using BOINC), the max speed according to i7z is 2.4 ghz. This processor has turbo profile 8/8/10/11, so it should be running at 3.2 ghz at max load on all cores.

I also have an i7-2600k in a desktop and it runs full turbo at max load under almost identical conditions (BOINC, same kernel, both on oneiric, etc). Something fishy is definitely going on...

---

### Post by xanadux on 2011-12-11
Here's a little more information. If I disable the stress test and wait a few minutes before running another test, the cpus do clock above 24x for a few seconds (around 30x, max should be 32x), then they taper down back to 24x. This was not the observed behavior about a month ago, at which time the turbo boost was sustained, so I suspect this is a distribution/kernel issue.

---

