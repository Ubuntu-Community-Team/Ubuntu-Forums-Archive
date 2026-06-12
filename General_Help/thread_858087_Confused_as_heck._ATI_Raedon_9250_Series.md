---
title: "Confused as heck. ATI Raedon 9250 Series"
date: 2008-07-13
forum: General Help
---

### Post by Haroskyline on 2008-07-13
Hello, I recently got into the whole linux/ubuntu thing a few weeks ago, but this problem with the ATI drivers is kind of scaring me away. I just recently (Yesterday) Decided to re-install it and try again. I installed the fglrx-4-3-0_8.28.8-2_i386.deb thing, and it seemed to install my drivers, but I have a few things I'm unsure about, so I have a few questions.

**1.** Are my drivers ACTUALLY installed? Or is the fglrx program only something that will allow me to download the driver and is not the driver itself.

**2.** When I installed the fglrx thing, it seemed to work, and now I have "ATI Control" in my applications, but when I click it, nothing comes up. (Same for ATI Catalyst Control Center)

**3.** Before, I was able to go into System> Preferences> Appearance> Visual Effects and actually be able to choose between the three options there, but now, when I choose anything other than "None" it gives me an error saying "Desktop effects can not be enabled".

**4.** I'm not sure if it will help much or not, but I ran compiz-check and this is what I got:

```
Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size 

```
Again, I'm brand new to using linux and ubuntu. Any help would be greatly appreciated.


PS. I've looked all around the forums and google for help.

:)

---

### Post by drs305 on 2008-07-13
EnvyNG is a gui-based app that can install nvidia and ati drivers. It's pretty straightforward.

To install:
```
sudo aptitude install envyng-gtk
```

To run:
System Tools > EnvyNG

---

### Post by Haroskyline on 2008-07-13
Hmm, I've never heard of it before. I'll try it.
I just hope I won't have to reinstall the entire Ubuntu operating system for the 5th time tonight. =/

EDIT: I ran it and it said ATI's legacy driver isn't supported by my operating system.
Hmm.

---

### Post by jake1017 on 2008-07-13
When I install my nvidia graphics drivers I simple right click the desktop, select Change Desktop Background. Then click the tab Visual Effects then click Extra. Then I get a message to enable nvidia drivers and from there it installs itself.

---

### Post by Haroskyline on 2008-07-13
Okay, so I seemed to have figured it out myself. :o

---

