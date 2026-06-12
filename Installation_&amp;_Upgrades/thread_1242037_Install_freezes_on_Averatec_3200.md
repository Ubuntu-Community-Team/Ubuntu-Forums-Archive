---
title: "Install freezes on Averatec 3200"
date: 2009-08-16
forum: Installation &amp; Upgrades
---

### Post by fongandrew on 2009-08-16
I have an old Averatec 3200 with 480MB of RAM I've been trying to install the 8.04 LTS on. I'm using the alternate installer because the regular one just dumps me to a console.

In order to keep the installer from freezing at 6% when doing a "base system install", I had to hit F6 and add the following boot options:

noapic nolapic ide=nodma acpi=off

But now it's freezing on different random packages on the software installation step. The CPU fan is still going pretty loudly, but it's been stuck on a single package for 4 hours. I'm somewhat at a loss at what to do here. I've already checked the integrity of the CD, so I doubt that's it.

I also tried Jaunty, but that won't even get me past the 6% "base system install" freeze. Any ideas?


I had earlier tried 9.04, but both the alternate and regular installer froze at 6% when doing the "base system install".

---

### Post by kruisa7 on 2009-08-16
Did you check the MD5sum of your CD before trying to install?  Bad CD's account for many problems trying to install, especially 'freezing on different random packages'.  Others have reported that the integrity check is not as good as the MD5sum.

Another possibility, check your BIOS settings, since you mention the problem with other versions.  Perhaps you have some unusual setting in your BIOS which is hindering a good install.

---

### Post by fongandrew on 2009-08-16
md5sum is fine. And nothing unusual in bios. It's an old system though running a Via chipset and has issues with its broadcom firmware. But I have everything running off a Cat5 cable, so I'm not sure if the latter is an issue. Is there some other option I can pass to boot that will help?

---

### Post by hantechbl on 2009-08-16
If you are in windows you could use unetbootin and use it on the hdd.

---

