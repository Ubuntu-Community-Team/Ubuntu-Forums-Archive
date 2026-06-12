---
title: "Sony pcg-n505ve (pcga-cd51) install"
date: 2009-06-08
forum: Installation &amp; Upgrades
---

### Post by TipTap on 2009-06-08
I believe I may have found a way to install ubuntu 9.04 on a Sony Vaio PCG-N505VE. Here is the hardware setup...

Sony PCG-N505VE
Sony PCGA-CD51 (PCMCIA)

Originally, the installer would bomb into BusyBox after detecting the PCMCIA CD-ROM drive. I thought this was strange since it booted from the drive. Nothing really worked to prevent the bomb of the install. I even tried version all the way back to Warty without any luck.

I figured it was a CD-ROM/PCMCIA issue so I research the forums but did not find anything concrete until I found the post below.

[http://mdsh.com/wiki/jsp/Wiki?Ubuntu:Install%207.04%20on%20PCG-Z600NE]("http://mdsh.com/wiki/jsp/Wiki?Ubuntu:Install%207.04%20on%20PCG-Z600NE")

I copied the contents of the 9.04 CD onto a USB flach drive. I booted the laptop with the CD <b>and</b> USB flash drive connected. The laptop booted from the CD and then continued to boot from the USB flash drive. After that I was able to get into the GUI. I did not add any commands to the boot options but did remove "quiet splash --" so I could see what was happening.

I am still testing but will keep you informed.

---

