---
title: "Installation of 8.10 stuck on Vostro 1400"
date: 2009-04-12
forum: Installation &amp; Upgrades
---

### Post by zhangmaster12 on 2009-04-12
I've checked the disk integrity and it passed. Burned @ 2x speed. 

Live CD works, internet, copying files, everything.

But upon installation, after files have been copied, the installation get stuck at checking battery state. Its been at this state for an hour.
[IMG]http://i129.photobucket.com/albums/p225/zhangmaster12/PIC-0282.jpg[/IMG]

System specs:
Dell Vostro 1400
2GB Ram
1.4 Ghz C2D
nVidia 8400G
Ubuntu im trying to install: 8.10 x86
Attempting to dual boot with windows 7 build 7068 (wubi doesnt work)

I didn't change any options with live cd boot, just followed the on screen directions. 

Btw, this was my second try. First try, at the same point, the video driver would stop working and I would get a message saying that my video driver has shut down 6 times in the last 90 seconds. 

HELP!

---

### Post by ispyamoose on 2009-04-12
Try unplugging the laptop battery for about 15-20 seconds so that it resets. I have a Vostro 1500 myself.

---

### Post by zhangmaster12 on 2009-04-12
WOOT!I stumbled upon [this]("http://www.uluga.ubuntuforums.org/showthread.php?p=6282441") thread and followed the instructions:

1) Boot live cd and enter safe graphics mode (f4)
2) Remove all installed nVidia packages in synaptic
3) Install with live cd

Going to install [these]("http://ubuntuforums.org/showthread.php?t=990978&highlight=love+nvidia") nVidia drivers

AND

Windows 7 Still works fine. Just when the GRUB loader pops up after bios, choose Vista/Longhorn bootloader

Funny how it was a display problem!

---

