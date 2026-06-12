---
title: "Can't boot SD card on power up (embedded)"
date: 2012-02-29
forum: Hardware
---

### Post by mjoyce on 2012-02-29
processor is a Marvel 88AP510
kernel 2.6.32.9 is in NAND flash
Ubuntu filesys 10.4 is on the SD card

I am having a problem booting a with the filesystem on an SD
card.  On the first boot from power on, I fail with the following
kernel messages:

[    3.317642] rtc-mv rtc-mv: setting system clock to 2012-02-29 20:43:03 UTC (1330548183)
[    3.325747] Root-NFS: No NFS server available, giving up.
[    3.331163] VFS: Unable to mount root fs via NFS, trying floppy.
[    3.337585] VFS: Cannot open root device "mmcblk0p1" or unknown-block(2,0)
[    3.344444] Please append a correct "root=" boot option; here are the available partitions:
[    3.352820] 1f00            4096 mtdblock0 (driver?)
[    3.357810] 1f01          520192 mtdblock1 (driver?)
[    3.362774] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(2,0)


If I then reset the board without a power cycle I succeed with
this:

[    3.340218] rtc-mv rtc-mv: setting system clock to 2012-02-29 20:43:21 UTC (1330548201)
[    3.365770] mmc1: new SDIO card at address 0001
[    3.370690] usb 1-1: configuration #1 chosen from 1 choice

How can I make the kernel see the new SDIO card on the first boot
from power on?

---

### Post by dandnsmith on 2012-03-02
How on earth did you build the SD card configuration?
It shouldn't be 'trying the mount the root fs via NFS' as NFS is a Networking File System, and you should be mounting the root filesystem directly from the card.

---

