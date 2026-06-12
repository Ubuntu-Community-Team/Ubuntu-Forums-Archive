---
title: "Small Form Factor/XPC support"
date: 2005-09-04
forum: Hardware &amp; Laptops
---

### Post by Linux BASHer on 2005-09-04
I will be building a box sometime soon (I hope). I've been looking for a stable user-friendly Linux distribution, and I have heard many good things about Ubunto. However, I want to build a small form factor/XPC system, like the Shuttle systems (It may a Shuttle, a BioStar or similar box), and I would like to know of any compatibility issues before I choose the hardware. Last time I built a small form factor unit, I was running Mandrake, which ran well, but there was no sound support (at least I couldn't get it to work).

I think it would be very useful to post up a small form factor PC compatibility guide here on the forums or/and on the wiki.

---

### Post by az on 2005-09-04
[QUOTE=Linux BASHer]
I think it would be very useful to post up a small form factor PC compatibility guide here on the forums or/and on the wiki.[/QUOTE]


Go right ahead!

As far as I know, half-hight pci cards do not need special drivers.  There should be no compatibility issues that would not already be there if you were using the same chipsets.

---

### Post by tranquility base on 2005-09-04
[QUOTE=Linux BASHer]I will be building a box sometime soon (I hope). I've been looking for a stable user-friendly Linux distribution, and I have heard many good things about Ubunto. However, I want to build a small form factor/XPC system, like the Shuttle systems (It may a Shuttle, a BioStar or similar box), and I would like to know of any compatibility issues before I choose the hardware. Last time I built a small form factor unit, I was running Mandrake, which ran well, but there was no sound support (at least I couldn't get it to work).

I think it would be very useful to post up a small form factor PC compatibility guide here on the forums or/and on the wiki.[/QUOTE]

I installed Ubuntu on my Shuttle SK41G yesterday.  I have never used Linux before yesterday, and am a total newbie.  The installation went well, and I am writing from my new Linux box.  The only **possible** problem is that things that are somewhat graphics intensive (like the screensavers) really bring my box to a halt, and are hard on the processor (causing the fan to speed up).  Given my hardware, this should not be happening.  I'm assuming that Ubuntu support for the on-board graphics is not right.  I may get an AGP graphics card that is supported by Ubuntu to try to fix the problem.  Otherwise the intallation went without issue, and it seems to be working fine.

---

### Post by jouni on 2005-09-05
[QUOTE=tranquility base]I installed Ubuntu on my Shuttle SK41G yesterday. [...]  The only **possible** problem is that things that are somewhat graphics intensive (like the screensavers) really bring my box to a halt, and are hard on the processor (causing the fan to speed up).[/QUOTE]

I also have a SK41G, and Hoary works fine, except for some graphics issues ([see my earlier post](http://www.ubuntuforums.org/showthread.php?t=62356)). That is: audio basically works (though I haven't tried anything fancy, just mp3 playback), a Logitech USB mouse works, two Firewire (IEEE1394) devices (a DVD+RW drive and a hard drive, both from LaCie) work, and Ethernet works.

Your graphics performance problems may be due to missing DRI (direct rendering infrastructure) support. If you're feeling adventurous, see the [HOWTO](http://ubuntuforums.org/archive/index.php/t-32043.html) on enabling DRI on Savage and report back how it worked.  :smile: (I haven't tried it myself, since I don't really need much graphics performance. If you're a total Linux newbie, this could be risky if it breaks your X configuration.)

By the way: are you seeing the flickering horizontal lines when scrolling windows that I reported in the earlier post?

---

### Post by jouni on 2005-09-05
[QUOTE=Linux BASHer]I think it would be very useful to post up a small form factor PC compatibility guide here on the forums or/and on the wiki.[/QUOTE]

There seems to already be one at [https://wiki.ubuntu.com/HardwareSupportMachinesBarebones](https://wiki.ubuntu.com/HardwareSupportMachinesBarebones).

---

### Post by Linux BASHer on 2005-09-05
[QUOTE=jouni]There seems to already be one at [https://wiki.ubuntu.com/HardwareSupportMachinesBarebones](https://wiki.ubuntu.com/HardwareSupportMachinesBarebones).[/QUOTE]

Ah, didn't find it-- It wasn't listed under "small form factor" or "XPC". That's great, though. We should use this thread and the wiki page to document small form factor specific compatibility and issues. I will add my own input once I get my own box.

---

### Post by tranquility base on 2005-09-19
[QUOTE=jouni]I also have a SK41G, and Hoary works fine, except for some graphics issues ([see my earlier post](http://www.ubuntuforums.org/showthread.php?t=62356)). That is: audio basically works (though I haven't tried anything fancy, just mp3 playback), a Logitech USB mouse works, two Firewire (IEEE1394) devices (a DVD+RW drive and a hard drive, both from LaCie) work, and Ethernet works.

Your graphics performance problems may be due to missing DRI (direct rendering infrastructure) support. If you're feeling adventurous, see the [HOWTO](http://ubuntuforums.org/archive/index.php/t-32043.html) on enabling DRI on Savage and report back how it worked.  :smile: (I haven't tried it myself, since I don't really need much graphics performance. If you're a total Linux newbie, this could be risky if it breaks your X configuration.)

By the way: are you seeing the flickering horizontal lines when scrolling windows that I reported in the earlier post?[/QUOTE]

No, I don't recall seeing flickering lines.  But graphics issues were taken care of by adding a GeForce MX4000 graphics card.  After installation, I had trouble with the drivers, so I just re-installed Ubuntu, and then installed the GeForce drivers from the repository, and everything works fine now.

---

