---
title: "Installation problem"
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by jyer on 2009-10-21
Dear All, 

I'm installing Ubuntu LTS 8.04.3 desktop i386 on a computer in order to use it as a server for an NGO. 

I do not have a floppy drive and thus disabbled it from the BIOS (it boots on CD-ROM and then HD). 

The Ubuntu CD boots fine, but when I either install or select try ubuntu without installation, Ubuntu loads until it reaches a screen with a bird drawn on the background (quite pretty, actually). 

Unfortunately, from there onwards, nothing happens. I tried to reboot many times, but the screen always freezes on the bird. 

The mouse works, insofar as I can move it (but not right click it). And I cannot use ALT + F2, F3, etc (just stays on the bird). I thus can't access the var/log files nor enter any commands. 

I did a verbalized instalation (with F6 then deleting splash and quiet), and everything seemed to be pretty smooth (except: 

```
44.984579 reported I/O error on device fd0, logical block 0
```

or something similar (I only have one screen). 

Last but not the least, the computer is pretty old (Fujistsu Siemens dating back to roughly 8 years ago, I estimate). 

Well, any tipps or, better, solutions are welcome. 

Best, 

Jyer

---

### Post by stlsaint on 2009-10-21
may be a bad hdd...can you try downloading the [alt.cd ]("http://www.ubuntu.com/getubuntu/downloadmirrors#mirrors")and installing from there?

choose your location than choose distro than select the alternate cd.

---

### Post by jyer on 2009-10-21
Thanks for your suggestion.

I'll try tomorrow when I'm back in the office ...

Forget to specify that the HDD seems to be working fine, since XP is running on it ...

cheers

---

### Post by jyer on 2009-10-27
Hey Stlsaint, 

That did the trick !

Thks a lot, 

jyer

---

