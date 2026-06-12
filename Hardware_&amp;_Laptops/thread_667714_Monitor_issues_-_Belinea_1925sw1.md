---
title: "Monitor issues - Belinea 1925sw1"
date: 2008-01-14
forum: Hardware &amp; Laptops
---

### Post by snoop2048 on 2008-01-14
Hi all, 

Ok, I have been using Ubuntu for 2 years and never posted here as I have found the answer I need by digging around. However, I have been defeated by the issues I am having with my monitor.

**Issue:** The display is wavy (going downwards) and I have literally tried everything I can find on the net. I think it is a refresh rate issue, 

Both Gutsy and Feisty and on 2 different machines

Current Hardware:
[INDENT]
Monitor: Belinea 1925sw1 1400x900. 
Graphics car: Nvidia 7600 (Asus) Proprietary drivers[/INDENT]

The specs for my monitor:

> Display colors       16.2 mill. colors
Synchronization	     31–83	kHz	horizontal,	56–75	Hz	vertical
Video band width	    135	MHz	(pixel	rate)
Ergonomic resolution 1440 × 900 (60Hz)

I cannot get Ubuntu to set this to 60hz, it offers me 50,51,52,53. 

I have tried the following:

[INDENT]- reconfigure with: dpkg-reconfigure xserver-xorg[/INDENT]

followed these howtos:

[INDENT]- [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
- [http://ubuntuforums.org/showthread.php?t=76387](http://ubuntuforums.org/showthread.php?t=76387)[/INDENT]

Not one to give up i took the drastic step of installing Madriva and the display was perfect. Shame Mandriva wasn't. So, I copied the relevant bits from /etc/X11/xorg.conf from the Mandriva build and pasted them in. This improved the display slightly, but its still slightly wavy. 

The Xorg.0.log claims to have the refresh rate correct (although Ubuntu does not in system > administration > screens ands graphics). Here is the relevant bit: 

```
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Setting mode "1440x900@60"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
```

I have also manually added a modeline for my monitor from [http://www.sh.nu/nvidia/gtf.php](http://www.sh.nu/nvidia/gtf.php) to no avail. 

My xorg.conf is attached (xorg.conf.txt) as is one from Mandriva that had it working perfectly (xorg.conf.mandrake.txt).

Any help would be greatly appreciated. I think my head is going to explode with this issue. A migration to Mandriva is not what I want, but I am loathed to to buy a new monitor.

Many thanks in advance.

---

