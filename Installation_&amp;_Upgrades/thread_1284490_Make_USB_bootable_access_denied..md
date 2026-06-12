---
title: "Make USB bootable access denied."
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by jahgamer189x on 2009-10-06
I'm using a usb drive to install ubuntu. I'm following a helpful tutorial and it says to make the usb stick bootable, and that I need to use fdisk to set the boot flag.

In the terminal I typed *fdisk /dev/sdb1 -a* but it came up with:
[I]
fdisk: invalid option -- 'a'

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
[/I]Any help please?

---

### Post by siulca on 2009-10-06
I did this yesterday except I did it the easy way using this free software:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

unetbootin makes a bootable USB of not just Ubuntu installs but most other Linux distros also. The only problem that I had was that the Linux version didn't work, I had to use the windows one.

Good luck I hope it helps. :)


PS> Any boot experts that can help with my issue? Here:
[http://ubuntuforums.org/showthread.php?t=1284305](http://ubuntuforums.org/showthread.php?t=1284305)

---

### Post by jahgamer189x on 2009-10-06
I actually tried Unetbootin about a week ago but I ended up getting stuck in a memory test thing and to get out I had to use my live cd. Problem was I didn't have one because I used Unetbootin.
Thanks for your help anyway!

---

