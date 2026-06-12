---
title: "So much lagggggg"
date: 2008-12-22
forum: Hardware
---

### Post by jeff_flynn on 2008-12-22
I am playing RuneScape and I don't know why my computer is lagging so much....any suggestions?

---

### Post by taurus on 2008-12-22
What graphic card do you have and have you installed a driver for it?

System -> Administration -> Hardware Drivers

---

### Post by kostkon on 2008-12-22
> **jeff_flynn said:**
> I am playing RuneScape and I don't know why my computer is lagging so much....any suggestions?
Maybe, it should be moved to the gaming sub-forum.

Anyway, what do you mean by saying that your PC is lagging (when playing this game)? Do you mean the graphics, sound, the networking, or something else?

What graphics card do you have and which driver are you using? Do you use the Java from Sun to run the game (I don't actually know if the game can be run with other than the Sun Java, I'm just asking)?

---

### Post by jeff_flynn on 2008-12-22
Actually the computer is lagging in general...What I mean is when I try to click on another window, it goes blank and does nothing for a few seconds....then eventually it brings up the other window...does this make sense?

---

### Post by jeff_flynn on 2008-12-22
> **taurus said:**
> System -> Administration -> Hardware Drivers

I go System -> Administration and I don't see anything with Hardwarein the name, although I do see "Restricted Drivers Manager" maybe this is it?


btw, I'm on Ubuntu 7.10 the Gutsy Gibbon

---

### Post by kostkon on 2008-12-22
> **jeff_flynn said:**
> Actually the computer is lagging in general...What I mean is when I try to click on another window, it goes blank and does nothing for a few seconds....then eventually it brings up the other window...does this make sense?
Yes, it makes. It means that there is a high possibility that you are not using the appropriate driver for your graphics card.

Which graphics card do you have?

Have you done what *taurus* suggested? That is, check if a driver for your card is listed in the restricted drivers utility?

---

### Post by taurus on 2008-12-22
> **jeff_flynn said:**
> I go System -> Administration and I don't see anything with Hardwarein the name, although I do see "Restricted Drivers Manager" maybe this is it?

btw, I'm on Ubuntu 7.10 the Gutsy Gibbon

For Gutsy, yes.  That's the one to check if there is a driver for your graphic card.

---

### Post by kostkon on 2008-12-22
> **jeff_flynn said:**
> I go System -> Administration and I don't see anything with Hardwarein the name, although I do see "Restricted Drivers Manager" maybe this is it?


btw, I'm on Ubuntu 7.10 the Gutsy Gibbon
OK. But please, could you please tell us which graphics card  you have? If you don't really know, then open a terminal (*Applications &#8594; Accessories &#8594; Terminal*) and give:
```
lspci
```
and post the output here.

---

### Post by jeff_flynn on 2008-12-22
i put in "lspci" into Terminal and got this

00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 12)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 12)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
02:09.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
02:09.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
02:0b.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)

---

### Post by kostkon on 2008-12-22
> **jeff_flynn said:**
> i put in "lspci" into Terminal and got this

00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 12)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 12)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
02:09.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
02:09.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
02:0b.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
OK, thanks. Are you sure you are not getting anything listed in *System &#8594; Administration &#8594; Restricted Drivers Manager*?

If not, then since you are using 7.10, I think it's safe to ask you to post the contents of your *xorg.conf* file here. Open a terminal again and give
```
gedit /etc/X11/xorg.conf
```
and post the contents here.

Also, in terminal give
```
apt-cache policy nvidia-glx
```
and check if it says that this package is installed or not.

---

### Post by jeff_flynn on 2008-12-22
So I enabled NVIDIA accerated graphics driver, and i restarted, and the ocmputer seems to be going 300x faster

---

### Post by kostkon on 2008-12-22
> **jeff_flynn said:**
> So I enabled NVIDIA accerated graphics driver, and i restarted, and the ocmputer seems to be going 300x faster
Nice :)

Everything OK then!

You could mark this thread as solved (if you believe so) by clicking the *Thread Tools* drop-down menu and selecting *Mark as Solved* (or something similar).

---

### Post by jeff_flynn on 2008-12-22
one last quick thing....Whenever i cycle between windows too many times, the runescape applet box goes grey...any ideas as to why it does this?

---

### Post by kostkon on 2008-12-22
> **jeff_flynn said:**
> one last quick thing....Whenever i cycle between windows too many times, the runescape applet box goes grey...any ideas as to why it does this?
Hmmm. I don't really know. Do you have Compiz enabled? That could be th reason for the grey box problem.

Or maybe it's just that Java responds very slowly when called to (re)paint the window and so when you move between windows very fast you see a grey background instead of the game's graphics.

---

### Post by jeff_flynn on 2008-12-23
OK, thanks. Are you sure you are not getting anything listed in *System &#8594; Administration &#8594; Restricted Drivers Manager*?

If not, then since you are using 7.10, I think it's safe to ask you to post the contents of your *xorg.conf* file here. > **kostkon said:**
> Open a terminal again and give
```
gedit /etc/X11/xorg.conf
```
and post the contents here.

Also, in terminal give
```
apt-cache policy nvidia-glx
```
and check if it says that this package is installed or not.

I did gedit /etc/X11/xorg.conf and it did nothing except open a blank page.

I did apt-cache policy nvidia-glx and I got the following:

jeff@jeff-desktop:~$ apt-cache policy nvidia-glx
nvidia-glx:
  Installed: 1:1.0.9639+2.6.22.4-16.12
  Candidate: 1:1.0.9639+2.6.22.4-16.12
  Version table:
 *** 1:1.0.9639+2.6.22.4-16.12 0
        500 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/restricted Packages
        500 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
        100 /var/lib/dpkg/status
     1:1.0.9639+2.6.22.4-14.9 0
        500 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/restricted Packages

---

### Post by jeff_flynn on 2008-12-23
Hi, I'm brand new to Ubuntu, I didn't chose to have Ubuntu, it was put on my computer because apparently windows fried my computer? i don't know. Anyways, the computer is running pretty slow and pissing me off...any ideas why it's being slow? sorry for being so vague...

---

### Post by taurus on 2008-12-23
What's the spec your machine and how much RAM does it have?  

What graphic card do you have and have you installed a driver for it?

p.s.  Why even create a new thread when you already have on active?

[http://ubuntuforums.org/showthread.php?t=1019180](http://ubuntuforums.org/showthread.php?t=1019180)

---

### Post by overdrank on 2008-12-23
Please do not create multiple threads on the same issue. Threads merged

---

### Post by jeff_flynn on 2008-12-23
Taurus, you'll have to bear with me, as I'm really green at Ubuntu, how do i find out how much RAM i have? and what are Specs? and how do i find out what graphic card i have? sorry

---

