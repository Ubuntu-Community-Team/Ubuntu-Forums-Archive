---
title: "Desktop freezes after 8.04 install"
date: 2008-09-04
forum: Hardware
---

### Post by jchstevens on 2008-09-04
I'm trying to find a version of linux to run on a desktop computer that I've had for a few years now. The computer spec is:
> Processors: 1
Processor speed: 505 MHz
Processor type: AMD-K6(tm) 3D processor
Physical memory: 320 MB
Video driver: NVIDIA GeForce FX 5200
The 8.04 LTS Desktop CD seemed to run fine as a live CD (albeit a little slow) so I installed 8.04 to my hard disk.  However, on rebooting and logging in, the computer seemed to freeze as it was drawing the desktop and I ended up with a clear desktop (no icons or menus). At this point the computer refused to respond to either mouse or keyboard so I had to switch it off!
If I monitor system messages during reboot using Ctl-Alt-F2 (or was it F1?), I get the following:
> [37.741303] ACPI: Unable to load the Systems Description Tables
[61.259415] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[61.365944] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[61.376400] sd 2:0:0:1: [sdd] Assuming drive cache: write through
[61.382933] sd 2:0:0:1: [sdd] Assuming drive cache: write through
At this point, I can't get back to the graphics screen but the computer does respond to Ctl-Alt-Del!
Can anyone suggest what the problem is?
Is my computer spec too low for 8.04?
What version of (ubuntu) linux could I reasonably run on it?
TIA,
Julian

---

### Post by jchstevens on 2008-09-22
Anyone have any ideas at all?
I'd really like to run Ubuntu on this computer, as XP runs SO s.l.o.w..l...y!
The desktop freeze seems to happen as the desktop is appearing and playing the default login sound. In fact, the sound stops part way through and from this point the screen freezes and the mouse and keyboard lock up.
Does this sound at all familiar to anyone?
TIA,
Julian

---

### Post by Sef on 2008-09-22
Check out [this thread]("http://ubuntuforums.org/showthread.php?t=715344"):

Here's a part of it #4:

> After much searching I found this solution to my **ACPI: BIOS age (1997) fails** error.
Go into your BIOS, locate the 'Power Management' section, and enable ACPI

Also check out this [website]("http://www.columbia.edu/%7Eariel/acpi/acpi_howto.txt").

---

### Post by jchstevens on 2008-09-22
Thanks Sef.
I'll give that a try when I get home tonight
Julian

---

### Post by jchstevens on 2008-09-22
Have fixed the ACPI setting in the BIOS, and am no longer getting that error on boot up.  However, the desktop is still freezing when I log in.
I've tried booting in recovery mode, and spotted the following error which I think is related to my sound card:
[  119.678003] snd-opl3sa2-pnpbios 01:01:00: activated
[  119.680455] snd-opl3sa2-pnpbios 01:01:00: disabled
[  119.692959] snd-opl3sa2-pnpbios: probe of 01:01:00 failed with error -2
[  119.702663] snd-opl3sa2-cpnp 01:01:00: activated

Could this be the problem, or does the fact that the final line reads activated mean that card/drivers are working correctly?

Thanks,
Julian

---

