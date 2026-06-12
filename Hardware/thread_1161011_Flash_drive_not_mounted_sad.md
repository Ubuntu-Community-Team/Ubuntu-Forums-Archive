---
title: "Flash drive not mounted :sad:"
date: 2009-05-16
forum: Hardware
---

### Post by Katman000 on 2009-05-16
For some reason, when I plug in my flash drive. Ubuntu detects it, but says it cant be mounted. What should I do, I need my backed up files!

---

### Post by Ropetin on 2009-05-16
> **Katman000 said:**
> For some reason, when I plug in my flash drive. Ubuntu detects it, but says it cant be mounted. What should I do, I need my backed up files!

Do you remember what file system it has on it?  If it's from the factory, or known to work on Windows it is probably FAT32.

If you plug the flash drive in, wait for the error to pop up then run the following two commands from a terminal, it should give you a little more information as to the problem.  Paste the output here, and we can take a look for you;

 ```
$ dmesg 
$ sudo fdisk -l 
```

(note, we probably only need the last 10 or so lines of dmesg)

---

### Post by Katman000 on 2009-05-27
Well I do remember that I first used my flash drive on my windows machine. I plugged in the commands and I got a ton of text. (below) It seemed as though everything was ok when i looked through it.  On the error it says that there is no media in the drive, shouldn't it still open? I tried a different flash drive and it wasn't even recognized. Soory for the long time between posts.

after dmesg:

[63715.793265] usbcore: registered new interface driver usb-storage
[63715.793276] USB Mass Storage support registered.
[63715.795281] usb-storage: device found at 4
[63715.795289] usb-storage: waiting for device to settle before scanning
[63720.792245] usb-storage: device scan complete
[63720.792803] scsi 2:0:0:0: Direct-Access     SanDisk  Cruzer           7.01 PQ: 0 ANSI: 0 CCS
[63720.793276] scsi 2:0:0:1: CD-ROM            SanDisk  Cruzer           7.01 PQ: 0 ANSI: 0

and then a lot of 

[63733.130434] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[63735.130864] sd 2:0:0:0: [sdb] Write Protect is off
[63735.130875] sd 2:0:0:0: [sdb] Mode Sense: 45 00 00 08

After the sudo fdisk -l :

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x16fd20ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3585    28796481   83  Linux
/dev/sda2            3586        4998    11349922+   5  Extended
/dev/sda5            4788        4998     1694826   82  Linux swap / Solaris
/dev/sda6            3746        3881     1092357   83  Linux
/dev/sda7            4737        4787      409626   82  Linux swap / Solaris
/dev/sda8            3586        3745     1285137   82  Linux swap / Solaris

Partition table entries are not in disk order

Thanks!

---

