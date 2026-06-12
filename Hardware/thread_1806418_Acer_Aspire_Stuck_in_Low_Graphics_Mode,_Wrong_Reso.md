---
title: "Acer Aspire Stuck in Low Graphics Mode, Wrong Resolution"
date: 2011-07-17
forum: Hardware
---

### Post by Flactivist on 2011-07-17
Hi Folks,

I've spent a couple weeks researching cases with similar symptoms, but haven't found solutions that fit my case.

**The Problem:** Upon upgrading from 10.04 (using Upgrade Manager, through 10.11) to 11.04 (x64), my Acer Aspire 5738z-4372 (Intel Graphics Chipset) is stuck in low graphics mode and an ugly resolution.

**The Symptoms:**

[LIST]
[*]Unity is not an option at login
[*]xorg.conf is empty, I've tried some different configurations but none help (and some even take out the GUI completely)
[*]sudo dpkg-reconfigure xserver-xorg does nothing
[*]Native resolution is 1366 x 768, I'm stuck in 1024 x 768. I tried adding 1366 in xrandr and got the error "xrandr: Failed to get size of gamma for output default"
[*]Back when I installed 10.04 I encountered the "blank screen on bootup" error, which was resolved with a "modeset" command in my grub settings, but I have encountered trouble recovering what that setting was (it appears to be gone from /etc/default/grub)
[*]Both the VGA and the display are listed as UNCLAIMED in the output of...a command I cannot remember. I'm sorry.
[/LIST]

**From lspci**
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)

```

I've read that this is not a drivers issue, that ubuntu has Intel drivers covered.

Please help! My laptop is usable but the display is so ugly now. Thanks so much.

---

### Post by Flactivist on 2011-07-19
Bump? If I can't figure this out I'm going to have to roll back to 10.04.

---

