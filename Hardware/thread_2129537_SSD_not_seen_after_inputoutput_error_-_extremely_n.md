---
title: "SSD not seen after input/output error - extremely needed help!"
date: 2013-03-26
forum: Hardware
---

### Post by khurtsiya on 2013-03-26
I have files backed up on Kingston 120 GB SSD. When try to copy to HDD - some files caused input-output error. After restarting system - SSD not seen anymore!

It is not mounting and not even seen in Disk Utility.

If I try to boot notebook with SSD pluged-in via USB - it "thinks" very slow and I can't even enter BIOS with it pluged-in - I should unplug and only than it will work properly.

I have very important files on that SSD. I believe they are not corrupted, should I only get access to that SSD.

Any thought very appreciated.

Thanks in advance!

---

### Post by Bashing-om on 2013-03-26
khurtsiya;

Admittedly does not sound too good. Let's look and see what ubuntu sees. With the ssd drive plugged in - terminal code:
```
sudo fdisk -lu
``` and take it from there.

---

### Post by tgalati4 on 2013-03-26
Open a terminal and page through dmesg:

```
dmesg | more
``` Spacebar to page forward, Control-C to quit.

Look for SSD-related error messages.

I'm not optimistic that you will be able to recover the drive.  It sounds like it is failing, and not in way that is recoverable.  If you can't mount it, then you can't use any recovery tools on it.

---

### Post by khurtsiya on 2013-03-27
I can't see SDD in output:

> mihail@mihail-laptop:~$ sudo fdisk -lu
[sudo] password for mihail: 

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00003361

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1448640511   724319232   83  Linux
/dev/sda2      1448642558  1465147391     8252417    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5      1448642560  1465147391     8252416   82  Linux swap / Solaris

Disk /dev/mapper/truecrypt9_1: 3220 MB, 3220963328 bytes
255 heads, 63 sectors/track, 391 cylinders, total 6290944 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2efa1a8c

Disk /dev/mapper/truecrypt9_1 doesn't contain a valid partition table

Disk /dev/mapper/truecrypt9_0: 3220 MB, 3220963328 bytes
255 heads, 63 sectors/track, 391 cylinders, total 6290944 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xea2e17e1

Disk /dev/mapper/truecrypt9_0 doesn't contain a valid partition table

Disk /dev/mapper/truecrypt9: 3220 MB, 3220963328 bytes
255 heads, 63 sectors/track, 391 cylinders, total 6290944 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

                  Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000139f1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   976768064   488384001   83  Linux


---

### Post by khurtsiya on 2013-03-27
Same here:

> mihail@mihail-laptop:~$ dmesg | more
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-39-generic (buildd@lamiak) (gcc version 4.6.3
 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #62-Ubuntu SMP Thu Feb 28 00:28:53 UTC 2013 (U
buntu 3.2.0-39.62-generic 3.2.39)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-39-generic root=UUID
=e8bd95a7-00f6-4c17-95f7-f0bf77c3efb8 ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d800 (usable)
[    0.000000]  BIOS-e820: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000020000000 (usable)
[    0.000000]  BIOS-e820: 0000000020000000 - 0000000020200000 (reserved)
[    0.000000]  BIOS-e820: 0000000020200000 - 0000000040004000 (usable)
[    0.000000]  BIOS-e820: 0000000040004000 - 0000000040005000 (reserved)
[    0.000000]  BIOS-e820: 0000000040005000 - 00000000a9b08000 (usable)
[    0.000000]  BIOS-e820: 00000000a9b08000 - 00000000a9d0a000 (reserved)
[    0.000000]  BIOS-e820: 00000000a9d0a000 - 00000000b8bbd000 (usable)
[    0.000000]  BIOS-e820: 00000000b8bbd000 - 00000000baeef000 (reserved)


---

### Post by dabl on 2013-03-27
This is a USB device?  What do you see if you boot the computer without the device connected, and then plug it in?  Try doing that, and if it is not automatically mounted, run dmesg again and look for errors at the point when you plugged in the SSD.

---

### Post by khurtsiya on 2013-03-27
Yes, USB. If I boot computer without it - it just boots normal, when I connect device - nothing happens. 

Here is dmesg output (I do not have a clue about it):

[http://www.wepaste.com/ssd/](http://www.wepaste.com/ssd/)

---

### Post by dabl on 2013-03-27
I see references to USB devices 3, 4 and 6 -- probably 6 is the SSD.  Try booting the computer, and when it is fully up, plug in the SSD, open a terminal, and issue ```
lsusb -v
```

In the output, you might (hopefully) find your device.  If not, try plugging it into a different USB port on the computer, and try the command again.

---

### Post by khurtsiya on 2013-03-27
As lsusb -v otput is to big, here is lsusb:

> mihail@mihail-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 0c45:648b Microdia 
Bus 002 Device 003: ID 0a5c:21d7 Broadcom Corp. 


---

### Post by khurtsiya on 2013-03-27
SSD is Kingston - can't see it here...

Also - when SSD worked fine - there was led always on after plugin in (and flashing when read or write), now it flashes one time and dies after plugin in.

---

### Post by dabl on 2013-03-27
That's bad.  If the USB device does not answer the query from the system, then I'm afraid it is a dead one -- I have never seen a method to bring it back to life.  :(

---

### Post by khurtsiya on 2013-03-27
Can that be caused by unplugin it without safe remove?

---

### Post by dabl on 2013-03-27
Usually it is data or filesystem damage that is caused by yanking the device without "ejecting" safely.  But, the basic USB "personality" should not be affected by removals -- I think it is something worse than mere filesystem corruption.   :-({|=

---

### Post by tgalati4 on 2013-03-29
It's possible that the USB enclosure is bad and that the disk is OK.  Try finding another USB enclosure.  If this SSD is a SATA device, then simply plug it into a desktop machine and try to read it.

---

