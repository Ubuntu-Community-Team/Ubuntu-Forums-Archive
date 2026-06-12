---
title: "Probably Easily Solved"
date: 2008-10-11
forum: Hardware
---

### Post by Lazar87 on 2008-10-11
Alright, so I've had my computer set up as a dual-boot between Ubuntu and Windows XP since last September.  I've has this issue for as long as I can remember, and finally decided to figure out how to resolve it.

I'm not exactly sure which version of Ubuntu I have (GRUB has it listed as "Ubuntu, kernel 2.6.20-15-generic" which doesn't seem accurate as a version number, but I really have no idea considering I haven't messed with Ubuntu since I set this up).  Here's my build list (figured I'd throw as much info in this post as possible):

> Mobo:  Asus M2N-SLI Deluxe
CPU:  AMD Athlon 64 x2 4600 (65W) Windsor 2.4 GHz
RAM:  Kingston 2 GB (2 x 1GB) 240-pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel
Video Card:  EVGA GeForce 8800GTS 320 MB
HDD:  Seagate Barracuda 7200.10 320 GB
DVD:  Pioneer DVR-212D

I select Ubuntu from GRUB and it boots the kernel.  After it boots the kernel, the screen goes black and stays black as it continues to load.  Then I hear the speakers get recognized.  It then loads for a little bit and stops, leaving me with a black screen.

First, I edited the kernel lines (below)  to remove "quiet splash".

> 
root(hd0,2)

kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=bc9241a5-2967-4aef-9ce7-7122519db2a2 ro *quiet splash*

initrd /boot/initrd.img-2.6.20-15-generic

quiet

savedefault

When I did this I received the following error:

> Failed to start the X server (your graphical interface). It is likey that it is not set up correctly. Would you like to view the X server output to diagnose the problem?

Yes
No

I pressed yes to see the X server output.  The first output it showed me said the following:

> 
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Oct 11 19:23:08 2008
(==) Using config file: "/etc/X11/xorg.conf"
(EE) VGA(0):  Driver can't support depth 24
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

I hit <OK>, at which point it asked if I wanted to view the detailed X server output as well, which I said yes.  I'm obviously not going to type this whole thing out (if you think something else from here would help I can just post with it later), but here's what it said at the bottom of the detailed output:

> (II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VGA(0): initializing int10.
(II) VGA(0): Primary V_BIOS segment is: 0xc000
(EE) VGA(0): Driver can't support depth 24
(II) UnloadModule: "vga"
(II) UnloadModule: "int10"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

So from here it basically confirmed my idea that there were some issues between my video card and Ubuntu.  I also started reading around and found out that this is a known issue.

I also attempted configuring my X Server and setting the driver to "vesa" but that didn't work either.  At this point I'm starting to get stumped.  I can only access Ubuntu through command line because of this problem (if I boot into recovery mode).  I don't know how to install the Linux drivers for my card from the nVidia site because I don't know how to do it either through command line or through XP, or if that would even resolve the issue.

Here's the output of lspci (again, not the whole output), which I also heard can help diagnose this issue:

> 02:00.0 VGA compatible controller: nVidia Corporation Unknown device 0193 (rev a2)

And here's the output of lspci -v:

> 02:00.0 VGA compatible controller: nVidia Corporation Unknown device 0193 (rev a2) (prog-if 00 [VGA])
Subsystem: eVga.com. Corp. Unknown device c815
Flags: bus master, fast devsel, latency 0, IRQ 11
Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
Memory at e0000000 (64-bit, prefetchable) [size=256M]
Memory at f8000000 (64-bit, non-prefetchable) [size=32M]
I/O ports at 8c00 [size=128]
Expansion ROM at fbfe0000 [disabled] [size=128K]
Capabilities: [60] Power Management version 2
Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
Capabilities: [78] Express Entpoint IRQ 0

Where do I go from here?

---

### Post by cariboo on 2008-10-11
Start your computer in recovery mode and a the menu try xfix. This should at least configure you your video card with the open source nv nvidia driver. Once you get to your desktop, go to System-->Administration-->Hardware Drivers. Select the recommended driver and follow the prompts.

Jim

---

### Post by Lazar87 on 2008-10-12
I'm not exactly sure what you mean about the xfix thing.  I did enter dpkg-reconfigure xserver-xorg and set the drivers to "nv", but that didn't do anything, so I wasn't able to get to my desktop.

---

### Post by Lazar87 on 2008-10-13
Could the problem be that I might be running a 32-bit version of Ubuntu?  Not sure about that really, or how to check, but someone suggested to me that that might be the problem.

Also, I'm pretty sure that it's an issue with the drivers, so how would I go about installing the correct drivers?

Any other ideas what the problem could be?

---

### Post by cariboo on 2008-10-13
To find out what version you have in a terminal type:

```
cat /etc/lsb-release
```

This will tell you what version you are running. If I had been paying a little more attention, I could have told you what version you are running. If you installed Ubuntu last September, you are running 7.04, or a beta version of 7.10.

My instructions won't work for that version. For your situation run:

```
dpkg-reconfigure phigh xserver-xorg
```

This may fix your problem, if it doesn't, try it again and select the vesa driver, this should allow you to boot to the desktop.

If all else fails you could always install Hardy 8.0.4.1, or wait three weeks and install Intrepid Ibex 8.10

Jim

---

### Post by Lazar87 on 2008-10-13
> To find out what version you have in a terminal type:

[quote]cat /etc/lsb-release

This will tell you what version you are running. If I had been paying a little more attention, I could have told you what version you are running. If you installed Ubuntu last September, you are running 7.04, or a beta version of 7.10.[/quote]

I ran this code and you were right, I'm running 7.04.

> My instructions won't work for that version. For your situation run:

[quote]dpkg-reconfigure phigh xserver-xorg

This may fix your problem, if it doesn't, try it again and select the vesa driver, this should allow you to boot to the desktop.[/quote]

I ran this command and this is what it returned:

> Package `phigh' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: phigh is not installed

Not sure where to go from there.

> If all else fails you could always install Hardy 8.0.4.1, or wait three weeks and install Intrepid Ibex 8.10

Wouldn't it just be easier for me to install Hardy instead of trying to fix this issue and then upgrade?  How would I go about doing that?

---

