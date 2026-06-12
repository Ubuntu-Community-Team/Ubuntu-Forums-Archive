---
title: "VirtualBox upgrade issue - weird graphics glitch"
date: 2009-07-18
forum: Installation &amp; Upgrades
---

### Post by voy on 2009-07-18
Hi, recently I upgraded packages including some graphic card drivers for the X.org server and VirtualBox to version 3.0.2.

I use virtualbox-3.0 from:

```
deb http://download.virtualbox.org/virtualbox/debian jaunty non-free
```

After the upgrade (restart including) I see a weird graphics glitch. Whenever I run VirtualBox in GNOME and switch to its window, the screen goes to inverted colors and looks all broken (not like when you enable negative in GNOME mind you, white is black, but otherwise it all looks really broken). What's strange is that when I switch back to another window, the colors go back to normal.

I tried recompiling the kernel modules for VirtualBox and reinstalling the whole package, but nothing has helped. I cannot take a screenshot, as the save screenshot utility seems to see everything alright. I also tried installing a new version of guest tools for my virtual Windows XP. Didn't help either.

No idea what else I could do, anyone ever had a similar problem? Help, please. I am desperate.

---

### Post by darco on 2009-07-18
You may want to head over to the Virtualization  forum and ask that question.

[http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

darco

---

### Post by setherd on 2009-07-23
> **voy said:**
> Hi, recently I upgraded packages including some graphic card drivers for the X.org server and VirtualBox to version 3.0.2.

I use virtualbox-3.0 from:

```
deb http://download.virtualbox.org/virtualbox/debian jaunty non-free
```After the upgrade (restart including) I see a weird graphics glitch. Whenever I run VirtualBox in GNOME and switch to its window, the screen goes to inverted colors and looks all broken (not like when you enable negative in GNOME mind you, white is black, but otherwise it all looks really broken). What's strange is that when I switch back to another window, the colors go back to normal.

I tried recompiling the kernel modules for VirtualBox and reinstalling the whole package, but nothing has helped. I cannot take a screenshot, as the save screenshot utility seems to see everything alright. I also tried installing a new version of guest tools for my virtual Windows XP. Didn't help either.

No idea what else I could do, anyone ever had a similar problem? Help, please. I am desperate.

FWIW I am having the exact same problem. and I can't find a solution either.:(

I'm running the latest version of Karmic here.

---

### Post by ptn107 on 2009-07-23
I'm running Virtualbox 3.0.2 on Ubuntu 9.04 x86_64 using the 185 series nVidia drivers.  I don't have this problem.  What video drivers are in use on your systems?

---

### Post by waster on 2009-07-25
same here with low-end radeon card

---

### Post by Shazaam on 2009-07-25
I had a different Vbox update graphics problem that MAY be related...
When I set the vbox guest video memory size (under VM>Settings>Display) to anything larger than 64 mb the virtual desktop would be rolled up to the top of the window like a window shade. Dropping it back to 64 cured it. I have an older AGP video card that may be the cause of the problem.
Try adjusting your guest video memory setting as a test.

---

### Post by wilbur.harvey on 2009-07-26
I am also having this problem.

I am running the latest Karmic, 64-bit, on a 2'nd generation Macbook Pro with ATI graphics. My i7 system with Nvidia doesn't have this problem. It just started with the upgrade to the 2.6.31-4 kernel and drivers. I tried reducing the video resolution as suggested with no change, and increasing it to the max, 128MB, and no change. I tried uninstalling compiz, no change. I have vbox 3.02. I tried re-initializing the xorg.conf to the default, and no change.

---

