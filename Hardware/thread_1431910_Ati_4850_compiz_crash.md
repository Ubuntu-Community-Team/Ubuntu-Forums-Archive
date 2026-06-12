---
title: "Ati 4850 compiz crash"
date: 2010-03-17
forum: Hardware
---

### Post by d34th on 2010-03-17
Hi!

I'm using an Ati 4850 with 10.2 drivers, but compiz crashes
I've noticed that it crashes (segfault) when I try to open a new window, maximize or some other things, but you can open a terminal and work for a while till you open another window (e.g. firefox)

There is the output when I run compiz from a terminal

```

Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.1.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x1024) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
Segmentation fault

```

fglrxinfo returns this
```
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series
OpenGL version string: 3.2.9551 Compatibility Profile Context
```

---

### Post by BbUiDgZ on 2010-03-17
> **d34th said:**
> Hi!

I'm using an Ati 4850 with 10.2 drivers, but compiz crashes
I've noticed that it crashes (segfault) when I try to open a new window, maximize or some other things, but you can open a terminal and work for a while till you open another window (e.g. firefox)

There is the output when I run compiz from a terminal

```

Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.1.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x1024) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
Segmentation fault

```

fglrxinfo returns this
```
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series
OpenGL version string: 3.2.9551 Compatibility Profile Context
```

ATI = world of pain
ditch the ATI card as ati has very poor support for linux, the OpenGL drivers are rubbish for want of a better word

---

### Post by Tikkyca on 2010-03-17
I have ATI graphics card everything works great on my model,but i heard for some of the graphic cards that are not good for compiz because driver sucks,i think the only way to fix that is to wait for good drivers to come out.

---

### Post by ghostborg on 2010-03-17
Wait till an update comes down preventing your system from booting.
This has happened to me several times over the years, always seems that ATI is behind the game with Linux.
I installed a cheapo Nvidia card from Officemax that has not let me down yet even though the ATI has superior specs.

I am tempted to give the ATI a try with Lucid but then I remember the last time I could not boot after an update at the most inopportune time.
JMHO:-({|=

---

### Post by Mawoon on 2010-03-17
It has nothing to do with your card but with the driver, 10.2 crashes on my 4650 as well, just download the 10.1. This one won't crash. 

PS: Don't listen to people that say you should throw away your ati card, once ubuntu 10.04 releases, better drivers will be released, since ati published their drivers while nvidia keeps it for themselves, so kernel developers need to reverse engineer it. ATI will do a lot better in the future :)

---

### Post by d34th on 2010-03-17
> **Mawoon said:**
> It has nothing to do with your card but with the driver, 10.2 crashes on my 4650 as well, just download the 10.1. This one won't crash. 

PS: Don't listen to people that say you should throw away your ati card, once ubuntu 10.04 releases, better drivers will be released, since ati published their drivers while nvidia keeps it for themselves, so kernel developers need to reverse engineer it. ATI will do a lot better in the future :)

10.1 seems to work fine, but I need at least 10.2 to run some OpenCL apps

---

