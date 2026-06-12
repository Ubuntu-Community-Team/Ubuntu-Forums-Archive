---
title: "Flash Issues in 9.10"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by D.horse on 2009-10-29
I am having some trouble getting a flash plugin installed on my roommates computer.  I finally convinced him to give ubuntu a whirl and i installed 9.10 on it in a dual boot fasion and everything went smoothly untill i tried to install a flash plugin.

When i try to install it through Mozzila (went to break.com and clicked on the pop-up that i need to install additional plugins)  and it says "could not find the package" for all three of the packages that it it shows as options to play flash.  I then went through Ubuntu Software Center and tried to install flash through that and it says "Not available for your hardware architecture".

Is his computer not able to play flash files under Ubuntu?  It works fine under windows.

Lenovo IdeaPad Y530

Intel Dual CPU T3400
2 Gigs Ram
160 GB HD

---

### Post by Sef on 2009-10-30
1) Did you uninstall the flash from break.com?

2) Are you using 32 or 64-bit Ubuntu?

---

### Post by D.horse on 2009-10-30
It was never able to install from break.com.  It says package could not be found.

I installed the 32-bit OS.....I believe.

 where would be the easiest spot to check 32/64 bit?

---

### Post by xXDynamosXx on 2009-10-30
If all else fails you can install flash player using the restricted extras found in the repository

```
Sudo apt-get install ubuntu-restricted-extras
```
installing this will install many of the restricted extras in ubuntu such as mp3 support, flash player 10, java as well as Microsoft Fonts such as comic sans. and other things :)

hope this helps you.

---

### Post by D.horse on 2009-10-31
I fixed the issue.  It turns out that you cannot download anything from the repository until you run an update.  Normally this is not a problem because it will inform you that you need to run one right as soon as you install Ubuntu, but i installed it on battery power and it does not automatically do the updates when running on battery. So i ran an update and everything worked great! 


:KS:KS

---

