---
title: "asus ha1101 gma500 display glitch"
date: 2015-05-16
forum: Hardware
---

### Post by denis0189 on 2015-05-16
hi to all i have a problem with my asus eeepc ha1101 with gma500 graphics card.

on the screen appear many glitch i post some img to make you understand.

[http://imgur.com/qykydtX](http://imgur.com/qykydtX)

[http://imgur.com/R4lfuzS](http://imgur.com/R4lfuzS)

[http://imgur.com/i4dixYH](http://imgur.com/i4dixYH)

with windows these glitch do not appear and do not think is a VGA or display problem...

sorry for my bad bad english

i hope there is someone who can help me

---

### Post by Vladlenin5000 on 2015-05-16
Hi and welcome.

What are those glitches exactly? It isn't at all clear from the snapshots you posted.
Please inform which Ubuntu variant and release number have you installed. And instead of just writing the computer's make/model you should add more info about the specifications. It shouldn't be up to the people trying to help you to do that homework of searching for the specs. I'll go ahead and post something I've found in the webs - *Please* confirm whether or not it matches your configuration and also inform how much RAM do you have and how much of that is assigned to graphics.
Note: It's a very underpowered machine according to current standards. It was already quite underpowered according to its own time standards (I would rather have an Intel based entry-level desktop from 2004/5) so, installing Linux requires careful planning, starting by the distro choice among the ones with the lightest desktop environments. 

[URL="http://www.cnet.com/products/asus-eee-pc-1101ha-seashell/specs/"]**Asus Eee PC 1101HA**



 [/URL]

---

### Post by denis0189 on 2015-05-16
thanks for the reply

i have try a lot of distro (ubuntu 14.04.2 (too much for my hardware) last linux mint cinnamon and mate edition (idem for ubuntu too much for my spec) now i try with xubuntu lubuntu and ubuntu mate all lts 14.04.2 (pretty fast and stable) and with all these distro i have the same problem with all) these glitch are quite difficult to snap in a picture i'm sorry for the quality but is my best.
i try to explain it.
it is almost as if pc works at low depth color like 8 or 16 bit instead of 24.
do you remember when in win 95/98 change the bit of color? 16 256 65k (16bit) and saw all the display with dotted color? thats the problem.

the spec of my ha1101 is:
cpu intel atom z520
gpu intel gma500 poulsbo res 1366x768 i don't know how much ram have VGA because i think is shared with ram
2gb ram
250gb hd

the actual distro installed is ubuntu mate edition 14.04.2 lts

with sudo lshw -c display i have this info:

description: VGA compatible controller
product: System Controller Hub (SCH Poulsbo) Graphic Controller
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 07
width: 32
clock: 33MHz
capabilities: pm msi vga_controller bus_master cap_list rom
configuration: driver=gma500 latency=0
resources: irq:22 memory:f3f80000-f3ffffff ioport:c800(size=8) memory: d0000000-dfffffff memory: f3f40000-f3ffffff

---

### Post by Vladlenin5000 on 2015-05-17
GMA500 is and always as been a problem...
Some reading: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

I suggest you use 12.04, supported until April 2017, which is the latest still supported release where GMS500 worked acceptably (or close to acceptable).

---

### Post by weatherman2 on 2015-05-17
Try this to get better drivers for the card, even in Ubuntu 14.04:

[https://launchpad.net/~thopiekar/+archive/ubuntu/emgd](https://launchpad.net/~thopiekar/+archive/ubuntu/emgd)

Also try this thread (still recent posts at the end);

[http://ubuntuforums.org/showthread.php?t=2107593&](http://ubuntuforums.org/showthread.php?t=2107593&)

---

### Post by denis0189 on 2015-05-20
thanks guys and sorry for the wait i had already seen those post and i tried to install emgd driver but i don't have found any solution yet.

with emgd driver the xserver crash after install...black screen and the only way to do something is to enter in recovery mode.

im editing the xorg.conf taking a cue from the example of thopiekar (the maker of driver).

the next step will be to downgrade to the version 12.04 if it does not work with the modified xorg.conf.

i don't have much time but i promise to write if there were news even though not think I have a lot of possibilities to make it work :-|

---

