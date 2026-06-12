---
title: "[ubuntu] Cannot mount remote Hard disk"
date: 2013-06-30
forum: Hardware
---

### Post by sflee on 2013-06-30
Dear all,

I am using ubuntu 12.04 and I have a hd named Buffalo HD-PCU2.
When I plug into the computer, it cannot mount the hd automatically.

**I type     lsusb, and have the following msg:**

Bus 001 Device 005: ID 0411:01d9 BUFFALO INC. (formerly MelCo., Inc.) 
Bus 002 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 002 Device 004: ID 0ac8:1101 Z-Star Microelectronics Corp. 
Bus 003 Device 002: ID 24ae:2001  
Bus 007 Device 002: ID 0c24:0022 Taiyo Yuden 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

**and then I type this    sudo fdisk -l, and then have msg:**

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c625a


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   616892415   308445184   83  Linux
/dev/sda2       616894462   625141759     4123649    5  Extended
/dev/sda5       616894464   625141759     4123648   82  Linux swap / Solaris



How to mount the hd again, I have important data inside the hd >.<"
Please help me~~~~

---

