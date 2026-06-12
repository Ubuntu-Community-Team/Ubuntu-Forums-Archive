---
title: "946gz with al1916w widescreen"
date: 2007-01-17
forum: Hardware &amp; Laptops
---

### Post by alamue on 2007-01-17
I'd post my var/xlog and xorg.conf... but i believe i have reached the edge of what i can do in eft.

I bought an Acer Aspire ASL310-EC352M Minitower on a whim due to a hefty rebate. While at it I also picked up an Acer AL1916w widescreen. Basically the first time i have bought a new computer. First one i didn't build myself since 1995.  Being that I've been round Linux  for some time I should have remembered... DON'T BUY HARDWARE ON A WHIM WITHOUT RESEARCHING, NO MATTER HOW CHEAP! 

I'm still happy with the purchase... but the saga is below. 

I was able to get the wireless going very fast by reading...
[http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom](http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom)
... although i didn't have to install the acpi... 

My trouble came with the video display. It seems the only way to get the widescreen to 1440x900 is to use the 915resolution package to rewrite one of the modes in my video bios.  Problem is that the current edgy build of doesn't support my graphics chip the 946gz. 

There is a newer build of the 915 package in Ubuntu but it appears to be for the Feisty build and requires a Feisty build of libc6. It really seems like a slippery slope. 

I had installed a newer deb version... which got me 

Selecting previously deselected package 915resolution.
(Reading database ... 99312 files and directories currently installed.)
Unpacking 915resolution (from 915resolution_0.5.2-9_i386.deb) ...
dpkg: dependency problems prevent configuration of 915resolution:
 915resolution depends on vbetool (>= 0.6.1); however:
  Version of vbetool on system is 0.6-1.1.
dpkg: error processing 915resolution (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 915resolution

I installed it using dpkg --force as i, perhaps mistakenly, thought that as they were likely the same version i wouldn't matter... but in the end i got...

(II) I810(0): Not using mode "1440x900" (no mode of this name)

I have a modeline that I made with info from my xorg log.  And i even tried modes 5c(bios mode i replaced) "5c" "(1440x990)" but it didn't like the name. I even tried specifying another mode for replacement. I should also mention that I am sure that 915 was starting before gdm.  This is all fairly a non-issue as I gummed up apt-get till i removed the debian 915 and did a apt-get -f.

I tried the ForceBIOS option with a newer i810 driver form xorg but that also failed. 

So unless someone has a good idea, I guess I am waiting for Feisty so i can have a proper aspect ratio.

---

