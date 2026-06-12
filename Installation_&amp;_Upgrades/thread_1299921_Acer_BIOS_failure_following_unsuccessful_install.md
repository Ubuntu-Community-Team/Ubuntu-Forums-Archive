---
title: "Acer BIOS failure following unsuccessful install"
date: 2009-10-24
forum: Installation &amp; Upgrades
---

### Post by theheed on 2009-10-24
Downloaded the latest build to install on an Acer Travelmate. I followed the screen prompt then 30 seconds later, the screen dies, well fades out. So I reboot and now the bios sequence will not kick in.
 
Looks like a brick thanks to Ubuntu, any ideas on how to recover

---

### Post by RJARRRPCGP on 2009-10-24
Ubuntu needs to disable the screen black out with the installer! :evil:

---

### Post by presence1960 on 2009-10-24
> **theheed said:**
> Downloaded the latest build to install on an Acer Travelmate. I followed the screen prompt then 30 seconds later, the screen dies, well fades out. So I reboot and now the bios sequence will not kick in.
 
Looks like a brick thanks to Ubuntu, any ideas on how to recover

I seriously doubt Ubuntu "bricked" your machine. I know that people when stuff happens they naturally blame Ubuntu. But usually 9 out of 10 times it is operator error.

P.S. just a hint: see this-> > Looks like a brick thanks to Ubuntu, any ideas on how to recover Do you think that may have something to do with the lack of responses for over 9 hours thus far? Hopefully lesson learned!

---

### Post by dreamingdarkness on 2009-10-25
Pull power cord.
Pull battery.
Let the PC sit for a couple minutes.
Put battery back in.
Put power cord back in.
Power PC back up.

See if that helps. Unless using a program specifically to do so, an OS of any type (Mac, Windows, Linux, Unix, etc) does NOT alter or impact the BIOS which is not stored on the hard drive and requires specific functions to be called to write or change it.

---

### Post by Mark Phelps on 2009-10-25
> **theheed said:**
> Downloaded the latest build to install on an Acer Travelmate.

WHICH latest build? 9.04? or 9.10 RC? Makes a difference.

> I followed the screen prompt then 30 seconds later, the screen dies, well fades out. 
Does your laptop have an optical drive? If so, you should have used the LiveCD boot to confirm that Ubuntu would even WORK on your laptop -- BEFORE doing the install. 

> So I reboot and now the bios sequence will not kick in.
 
Looks like a brick thanks to Ubuntu ...

Ubuntu does NOTHING to the BIOS sequence. Period.  What it does DO is modify the MBR so that, at boot time, it reads some files to find out which OSs you have on the machine and where they are located.

Since 9.04 and 9.10 use COMPLETELY DIFFERENT boot handlers, we need to know the specific version you installed.

---

