---
title: "Problems with HP Pavillion dv6184ea (headphones jack, no screen lock on lid close)"
date: 2006-11-22
forum: Hardware &amp; Laptops
---

### Post by m4dd0c on 2006-11-22
Hello.

I'm having some troubles with ubuntu (edgy) on my new laptop.

1)The headphones jack is not working as it should. Microphone not working.

I get very low volume out of the headphones, and music keeps playing in the speakers. I've been trying to find a solution to this problem, and there seems to be others having similar problems - but I haven't yet found a solution.

$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

from lshw:
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel
             resources: iomemory:de300000-de303fff irq:66

The devices is listed as "Conexant High Definition Audio Driver" on HP's site.

Also nor the internal microphone or the microphone jack is working at all, as it seems.

In the volume control I only got two slides: Master and PCM.

2) Screen lock on laptop lid close.

When I close the laptop lid, the screen isn't locked. I've looked in Systtem -> Settings -> Power management, and put the screen lock alternative in the screen saver setup on; but still no screen lock on lid close.

This worked fine, without configuration, in dapper!

3) Minor problems.

* I can no longer close conversations in gaim with the escape-button.
* How do I get firefox to use the old system for tabs? The new one is kind of annoying when you have alot of tabs opened.
* The play and skip forward/backward-buttons on the remote control is not working. (otherwise the remote control worked really fine "out of the box"!)

4) Not yet tested.

* Video out. (need a s-video -> composite converter, none was shipped with the laptop and I've lost mine)
* WLAN. (I haven't got a AP to test it against. The WLAN card is recognized by ubuntu, but the LED on the computer shows it as off.)

As a last word I can say that it really was easier to install ubuntu on this machine than Windows XP Professional (the MCE installation was really bloated, and the partition couldn't be shrunked), as I had to use a USB floppy drive just to be able to find the harddrive (and I still haven't gotten the sound to work, at all, in win xp).

---

### Post by sarc on 2006-11-23
I'd sure as hell would like to find out too (HP pavilion dv2000)

---

### Post by lexarrow on 2007-05-26
for the sound problems try [this]("http://ubuntuforums.org/showthread.php?t=455147")

---

