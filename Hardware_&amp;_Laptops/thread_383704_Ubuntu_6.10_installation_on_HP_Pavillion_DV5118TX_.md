---
title: "Ubuntu 6.10 installation on HP Pavillion DV5118TX Error"
date: 2007-03-13
forum: Hardware &amp; Laptops
---

### Post by amanjsingh on 2007-03-13
Hi,

I could install but could not run Ubuntu on my laptop. Although the Live CD runs properly but after installation, Ubuntu does not boot into GUI stays on the command line and the package X11 is missing so I cannot use any of those commands like **init **or **startx**.


The thing is that Live CD works fine. It boots but shows this error in the start

PCI cannot allocate resurce region 7 of bridge 0000:001C.0
PCI cannot allocate resurce region 8 of bridge 0000:001C.0
PCI cannot allocate resurce region 6 of bridge 0000:001C.0
PCI cannot allocate resurce region 5 of bridge 0000:001C.0
PCI cannot allocate resurce region 4 of bridge 0000:001C.0
PCI cannot allocate resurce region 0 of bridge 0000:001C.0

And then it boots in GUI but the same installation on hard drive fails to boot into GUI.

I want to know Is there anyone who has installed Ubuntu on laptop - [B]HP Pavillion DV5118TX

[/B]Specs -
NVDIA Ge Force Go 7400
Intel pentium duo core T2300
SATA HDD 100GB (hts541010g9sa00)
I already have Windows XP (home) on it.

Help!

Thanks
AJ

PS - I am new to linux and I have tried installation 3 times after which I restored my system to windows XP again. :-(

---

### Post by TwoWordz on 2007-03-13
Hi!

Just to make sure, you successfully booted the ubuntu live cd, and you have used the install icon on the desktop?

Did the install finished successfully and ejected the cd?

Which cd version did you use?

TW

---

### Post by amanjsingh on 2007-03-13
> **TwoWordz said:**
> Hi!

Just to make sure, you successfully booted the ubuntu live cd, and you have used the install icon on the desktop?

Did the install finished successfully and ejected the cd?

Which cd version did you use?

TW

Thanks a lot for your reply.

Version number of the CD -  I am not sure. I downloaded it sometime back.
yes, the CD was successfully installed and I had the install icon.

I have tried non-live CD's also. Same errors.

---

### Post by TwoWordz on 2007-03-13
Is there an option in your bios to set the IDE mode (or SATA) to compatible?

TW

---

### Post by amanjsingh on 2007-03-13
> **TwoWordz said:**
> Is there an option in your bios to set the IDE mode (or SATA) to compatible?

TW

It has an option - **SATA Support [Enable/Disable]**

It is enabled right now and has always been enabled. Should I disable it?

Some people do say that it is a SATA problem with me and some say it is nVidia. I am confused.

Thanks for your help.
-AJ

---

### Post by TwoWordz on 2007-03-14
Please be more specific about what are the final lines of text displayed on your computer when trying to boot ubuntu. 

TW

---

### Post by amanjsingh on 2007-03-14
> **TwoWordz said:**
> Please be more specific about what are the final lines of text displayed on your computer when trying to boot ubuntu. 

TW

I installed Ubuntu safely this time. Thanks for your help. :-)

---

