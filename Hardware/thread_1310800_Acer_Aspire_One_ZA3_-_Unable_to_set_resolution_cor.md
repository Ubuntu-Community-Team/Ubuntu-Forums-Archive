---
title: "Acer Aspire One ZA3 - Unable to set resolution correctly in 9.10 Karmic"
date: 2009-11-02
forum: Hardware
---

### Post by CheeseEatingBulldog on 2009-11-02
I have installed 9.10 on my gf's Acer Aspire One ZA3. Everything works out of the box except that the resolution is wrong. It gives me 1024x768, which cannot be changed in "Display". 

I installed the normal desktop version of Karmic, and not the netbook remix (hate the interface). 

In Jaunty the solution was to add the ppa mobile team's repositories and install a psb kernel. However on the mobile team's site now it states: 

"You can update your system with unsupported packages from this untrusted PPA by adding **ppa:ubuntu-mobile/ppa**  to your system's Software Sources."

Which gives an error that **ppa:ubuntu-mobile/ppa** is an invalid source. So no idea how to add that. Changing the previous jaunty repo to karmic doesn't work. 

I had another thread in beginner talk, but the only solution someone could give was to reboot multiple times after turning off compiz. Firstly compiz doesn't even run on the ZA3 and I rebooted about 10 times (not that I expected anything to change) no to avail.

Is there anyone who can help?

---

### Post by CheeseEatingBulldog on 2009-11-03
Bump. Anyone?

---

### Post by Peter09 on 2009-11-03
Have you tried booting into recovery mode and selecting the option to reset the video?

---

### Post by CheeseEatingBulldog on 2009-11-03
It is not a reset, as it is a clean install, this is what it forces me to use. The old dpkg xorg reconfigure doesn't work. You can't edit the xorg file by hand anymore...and the display setting in ubuntu just give you the one option.

---

### Post by CheeseEatingBulldog on 2009-11-07
Anyone have an idea yet?

---

### Post by CheeseEatingBulldog on 2009-11-07
I think it is somewhere in the driver, the intel one is installed, yet a vesa driver is running as seen here by compiz-check:

```
Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)
 Driver in use:         vesa
 Rendering method:      AIGLX


```

So how does one configure the display these days. Editing Xorg.conf is out as it no longer is there. The display option gives only one choice so where is an override for the system?

Surely "Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)" is nothing more than an itel chip, so why is the driver not active? Hardware drivers give no propriatry options either btw

---

### Post by CheeseEatingBulldog on 2009-11-07
Right, fixed it ...found [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/426791]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/426791") this bug, which lead me to [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo") that fix. Easy peasy. 

Download the the packages, of which I think 3 .deb files. Install them and follow the guide. There is no xorg.conf, but I put mine (created) in the usual /etc/X11/ directory. Reboot and wonderful resolution!

EDIT: I tried [http://ubuntuforums.org/showthread.php?t=1014534&page=76]("http://ubuntuforums.org/showthread.php?t=1014534&page=76") the xorg.conf at the bottom of the page, as another thread suggested it might add 3d and compiz. It didn't as it gave me a distorted disply, but then compiz didn't work for me in jaunty either.

---

### Post by james.exe on 2009-12-05
Hi, I have an AAOZA3 as well and I'm trying to get the 1366x768 resolution working correctly. I've thoroughly read the guide, but it's just not working out for me. With the old method, I try running the commands to add the PPAs but I get this as an output for each one:
bash: /etc/apt/sources.list.d/ubuntu-mobile.list: Permission denied
With the new method, I run the first code and later at the prompt screen, when I try to run the wget code, it tells me that "http://gma500re.altervista.org/" could not be resolved. I figured that maybe my computer is not connected to the internet. I usually have to input my keyring in order to receive the wireless internet connection from my router. Is there any way to connect to the internet from the prompt screen? If that's not the problem, then any ideas on how to get my screen resolution working properly?

---

