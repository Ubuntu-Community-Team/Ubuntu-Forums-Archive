---
title: "AMD and turbo core"
date: 2013-07-31
forum: Hardware
---

### Post by wingnut2626 on 2013-07-31
Hi everyone!  I have a AMD Phenom 2 1045T (2.7Ghz, 3.2 Turbo)  That I have gotten overclocked to 3.38Ghz via upping the FSB on my motherboard (200-250).  I turned on the 'turbo core' feature and is shows that the turbo core will run at 4.0Ghz.  I then ran a benchmark where all 6 cores were at 100% and 'lscpu'  still has the speed at 3.38Ghz.  Will I actually see that 4 Ghz turbo core speed, and if so when?

---

### Post by cebif on 2013-07-31
With AMD CPU's Bulldozer, Piledriver and Phenom too, the turbo core only turns on when other cores are in lower usage. This is so total power won't get above maximum for the CPU. Since you were running a benchmark that runs all cores at once, the total power would be exceeded if they ran at turbo.
[http://www.microcenter.com/tech_center/article/6009/INFO_What_is_AMD_Turbo_CORE_Technology](http://www.microcenter.com/tech_center/article/6009/INFO_What_is_AMD_Turbo_CORE_Technology)

---

### Post by Yellow Pasque on 2013-07-31
> Will I actually see that 4 Ghz turbo core speed?
No, cpufreq won't show the turbo speed. I forget if AMD has its own special tool, but I know Intel has a special tool for their CPU's: [https://code.google.com/p/i7z/](https://code.google.com/p/i7z/)

---

### Post by wingnut2626 on 2013-07-31
ok but it will still exist?  I'm just confused about that.....

---

### Post by Yellow Pasque on 2013-07-31
Yes, it will still exist if you have it enabled in the BIOS, but you won't "see" cpufreq reporting it. You may want to run a single instance of cpuburn to test out stability of a single-threaded workload (where the turbo should be active). That sounds like a healthy OC. I hope you have good RAM, PSU, cooling etc.

---

### Post by wingnut2626 on 2013-07-31
Oh yeah, every component is aftermarket, and the CPU itself is liquid cooled.

---

