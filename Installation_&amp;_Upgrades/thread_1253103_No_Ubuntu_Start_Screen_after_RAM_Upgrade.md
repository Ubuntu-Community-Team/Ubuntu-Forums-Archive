---
title: "No Ubuntu Start Screen after RAM Upgrade"
date: 2009-08-29
forum: Installation &amp; Upgrades
---

### Post by ifraser on 2009-08-29
Hey all,

Just upgraded from 2GB to 4GB (same make/model/spec RAM sticks) on my desktop and now can't boot into Ubuntu.  My Vista partition works fine, exactly as it did, but now Ubuntu goes through the loading screen and then goes black, not reaching the login screen.  I ran a *memtest* from the GRUB menu and everything came back fine - it also displayed the new amount of RAM properly (40** MB or whatever 4GB actually is)  Any ideas?  Much appreciated.

I can't find a similar thread, but if there is one please direct me to it and we can close this thread.

Running Ubuntu 9.04

---

### Post by SunnyRabbiera on 2009-08-29
If you get the login screen I would not worry about it, maybe its booting so fast that it skips the boot up screen...
sometimes RAM upgrades do that :D

---

### Post by ifraser on 2009-08-29
> **SunnyRabbiera said:**
> If you get the login screen I would not worry about it, maybe its booting so fast that it skips the boot up screen...
sometimes RAM upgrades do that :D

I don't get to the screen!  That's my problem....

---

### Post by inobe on 2009-08-29
when ever i add more ram' i reset the cmos' then of course set time and date and exit saving changes.

given the situation it's worth a shot.

---

### Post by ifraser on 2009-08-29
Update:  Clearing the CMOS did nothing besides let me practice popping out my motherboard battery (Gigabyte motherboards apparently don't have jumper pins).  However, I entered recovery mode and did the autofix on X and that *seemed* to fix the problem (I can boot to Ubuntu desktop now), but it appears some display issues have appeared.  E.g. resolution is slightly off, etc.

---

### Post by inobe on 2009-08-29
when you did the x thing it reconfigured your xserver/ xorg.

do you have onboard video ?

in terminal could you get your

```
lspci
```

info and post it

---

### Post by ifraser on 2009-09-20
After much searching the problem ultimately boiled down to something as simple as outdated BIOS.  After flashing up to the most recent version, nearly all problems have been fixed sans the one here: [http://ubuntuforums.org/showthread.php?p=7982254#post7982254](http://ubuntuforums.org/showthread.php?p=7982254#post7982254)

Thread is now solved.

---

