---
title: "Boot: mounting ext4 takes 5 seconds? Why?"
date: 2011-03-09
forum: Hardware
---

### Post by Markus72 on 2011-03-09
Hi all,

I have a brand new SSD and am very frustrated because there is a delay during boot where there seems to happen nothing:

```
[    2.386198] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.386268] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    7.429068] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    7.656550] EXT4-fs (sda1): warning: maximal mount count reached, running e2fsck is recommended
[    7.657066] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    7.663148] udev[431]: starting version 163

```

What the hell is happening there? Any idea how to debug / reduce the delay?

Thx
Markus

PS: I have a comparable behaviour during shutdown... ok it's still quick, but not enough ;-)

PPS: Lenovo T500, Kubuntu 10.10 64Bit

PPPS: shutdown is quicker when using a fresh install

---

### Post by fjgaude on 2011-03-09
With respect to boot time, after the BIOS knows the MBR drive and where it points, we get **Operating System Loading...**

Then there is a wait while, I believe, the computer regenerates the **grub.conf** file. This all started sometime during the updating of Ubuntu 10.10. I know it is in 11.04. Maybe when 11.04 is released in late April the de-bug code in **grub** will go away and things will get back to normal, which is quick, quick for booting.

I'm sure the programming team knows of this issue and will be fix it. <smile>

---

### Post by Markus72 on 2011-03-09
Ah ok! Then I'm looking forward (which I do anyway) to the new release!

---

### Post by Markus72 on 2011-03-09
By the way - I remembered having installed the alpha of 11.04 and checked the behavior there...

```
[    2.239087] sd 1:0:0:0: [sdb] Attached SCSI disk
[    2.671774] EXT4-fs (sdb3): mounted filesystem with ordered data mode. Opts: (null)
[    4.970367] EXT4-fs (sdb3): re-mounted. Opts: errors=remount-ro

```

So, this looks much quicker than the quote at the beginning of the thread - even though that 11.04 was booted from a comparably slow laptop 5.400 rpm hdd while the 10.10 was on a 285 mb/s SSD...

Looks promising! Good hint, fjgaude.

Markus

---

### Post by fjgaude on 2011-03-11
Say, I just noticed if I don't have my CDROM drive as the first to boot, then a hard drive, things sped up by 22 seconds. It seems the OS tries to find a bootable OS on the CDROM drive and it takes awhile to do that. If you change in your BIOS to use your Hard drive then the boot time is quick.

From here on out I'll F12 if I wish to use a CD from which to boot. That F12 shows a menu with USBs, etc. Your machine might have a different F function key to us.

---

### Post by Markus72 on 2011-03-12
Hi, just changed the boot order without a difference...

PS: even removed the hotplug DVD drive completely... also no difference

---

### Post by Markus72 on 2011-04-28
No fun - I just upgraded to Kubuntu 11.04.... again 6 seconds idling... any ideas?

```
[    2.425933] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.425948] sd 1:0:0:0: [sdb] Write Protect is off
[    2.425951] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.425969] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.431144]  sdb: sdb1 sdb2 sdb3 sdb4
[    2.431489] sd 1:0:0:0: [sdb] Attached SCSI disk
[    8.214694] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    8.464554] <30>udev[395]: starting version 167
[    8.514398] lp: driver loaded but no devices found
[    8.518091] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    8.586149] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[    8.633823] type=1400 audit(1304020953.822:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=566 comm="apparmor_parser"

```

---

### Post by fh_scott on 2011-10-19
Hey did you ever find any resolution to this? I just upgraded to 11.10 and am seeing this exact behavior on my HP EliteBook.

---

### Post by Markus72 on 2011-10-22
Hey, no - still the same behaviour. :-(

---

