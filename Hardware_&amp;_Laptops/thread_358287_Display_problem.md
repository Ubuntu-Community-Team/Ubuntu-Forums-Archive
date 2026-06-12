---
title: "Display problem"
date: 2007-02-10
forum: Hardware &amp; Laptops
---

### Post by theriverhorus on 2007-02-10
I'd like to switch from XP to Linux and have booted Ubuntu 6.1 from live DVD to evaluate.  Everything seems to go well until the desktop screen appears. The monitor begins to streak with vertical lines and dots if I cursor over or select any desktop items.  Problem gets worse until eventually all text and icons become illegible and then everything simply locks up. The only way to recover is to turn power off. Even after rebooting into XP, the monitor will occasionally still have lines. Sometimes takes several reboots to recover to normal. Can anyone suggest a solution? I am anxious to run Ubuntu Linux but cannot resolve this initial display problem.  I've also tried Linspire and SimplyMephis on Live CDs or DVDs and do not have his display problem on either of them.  I have also tried SUSE and I have the same display problem on that version of Linux that I have with Ubuntu. 

I am entirely new to Linux and haven't a clue how to determine or correct this problem.   
   
Here are the specifics about my system:

Pentium 4.24 Ghz 800FSB
Gigabyte 81848P-G motherboard
768 mb ram
200 GB HD
Video Card: NVIDIA GeForce4 MX 440
ADVUEU 723A 17" LCD Monitor

Any assistance or suggestions will be much appreciated.

---

### Post by banditti on 2007-02-10
from CLI

```
sudo apt-get install automatix2
```

That will install automatix under your applications menu.  Install the NVIDIA drivers from there.  It should help.

---

### Post by theriverhorus on 2007-02-11
Can You Be More Specific How I'm To Use This Code And How I Am To Install Drivers "from There."

---

