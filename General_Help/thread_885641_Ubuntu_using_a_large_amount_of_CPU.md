---
title: "Ubuntu using a large amount of CPU"
date: 2008-08-10
forum: General Help
---

### Post by javeh on 2008-08-10
Hi Im a total linux newbie I'm afraid so bare with me.

Ive just installed ubuntu dual booting with winxp, i had some problems with the installation and i had to use the all_generic_ide command to get it to work. 

At the moment system monitor is saying ~45% CPU usage and all i have open is firefox and amarok (not even playing). Sometimes when i try and use the computer it becomes unusable - it pauses and cpu usage spikes to 100%

I have had no such problems with XP which comes as a shock - its supposed to be the other way round right?

Im using 32bit on a 64bit system.
athlon 64 3500+
1GB mem
2 Ide HDDs and 2 satas
ATI radeon X800

Thanks very much

---

### Post by Sycron on 2008-08-10
You may try htop  to see real CPU usage. System monitor is a bit buggy.

install htop:
```
$ sudo apt-get install htop
```
and then run it
```
$ htop
```

---

### Post by javeh on 2008-08-10
Cheers for that,

htop is giving much lower percentages now! 6-11% with firefox and amarok playing. but it still freezes occasionally, could it be because the mp3s im playing are off a different (and ntfs) drive? i only say this because of the issues i had installing

---

### Post by Sycron on 2008-08-10
no, it's normal.

---

