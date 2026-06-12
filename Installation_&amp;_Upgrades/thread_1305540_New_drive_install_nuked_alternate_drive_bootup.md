---
title: "New drive install nuked alternate drive bootup"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by Vhalidictes on 2009-10-29
Sorry for the post - I tried to fix this myself, but Google just isn't working.

Problem Statement:
I added a new HDD today and installed Ubuntu 9.10 and it works great! I even got many (Windows) games working within ~2 hours. 

However, Window XP no longer boots. GRUB lists Windows XP as a bootup option but when it is selected I get the response "Error: Invalid Signature. Press any key to continue" and I am returned to the OS selection menu.

PC is a Core2 (Intel) system with onboard "fakeraid" (ICH9R)

BIOS:
RAID5 is set as boot disk.

Drive Map:
Hd0 (RAID5 member) 
Hd1 (RAID5 member)
Hd2 (RAID5 member)
Hd3 (RAID5 member)
Hd4 (standalone disk - added today)

Partition Map:
RAID5 array: "C" 250GB - Windows boot, "D" 1.8TB - data
Standalone Disk: 470GB ext3 partition, 30GB swap partition (autocreated by Ubuntu install)

GRUB entry for Windows XP: 
drivemap -S (hd0) ${root}
chainloader +1

What are some of the things that I can do to troubleshoot this? Is there any information that would be helpful that I can get?

Also, note that I cannot run grub from the terminal. I get the friendly "sudo: grub: command not found" response. I've checked the /BIN and /BOOT hierarchy, and I simply cannot find the executable. 

The Synaptic Package Manager lists that "grub-pc" is installed (and that it, contrary to the name, is actually grub2), but I can't seem to access it.

Thanks,
-> Vhal.

---

