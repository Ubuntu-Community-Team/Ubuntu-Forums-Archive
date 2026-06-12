---
title: "External HDD and USB Thumbstick won't mount"
date: 2008-06-25
forum: Hardware
---

### Post by noah_balboa on 2008-06-25
Ok, first off, I don't even know what "mounting" really is...just seems to make HDD's visible.

Anyways, I plugged in a new external HDD, and it couldn't mount, said I had to "force" it through a bunch of jibberish. Same thing with a used USB thumbstick. However, it does recognize me SDHC card no issues. How can I fix this?

---

### Post by tamoneya on 2008-06-25
okay I want to get a sense for your partitioning scheme and such so if you can post the output of the following command in terminal (applications -> accessories -> terminal):```
sudo fdisk -l
```You can copy it out of terminal with ctrl-alt-c.  Then paste into the forums.

---

### Post by noah_balboa on 2008-06-25
Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

---

### Post by tamoneya on 2008-06-25
in my post above the "-l" is a lowercase "L" not an "I" or a number "1"

---

### Post by noah_balboa on 2008-06-25
whoops, sorry.

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0e045244

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15368   123443428+   7  HPFS/NTFS
/dev/sda2           18369       19457     8747392+   7  HPFS/NTFS
/dev/sda3           15369       18368    24097500    5  Extended
/dev/sda5           15369       18238    23053243+  83  Linux
/dev/sda6           18239       18368     1044193+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by tamoneya on 2008-06-25
you need to do this while the harddrive and thumbstick are plugged in.  That way I can tell you how to mount them.

---

### Post by noah_balboa on 2008-06-25
Ok. Forget the thumbstick for now. I'm in Linux right now, and the external drive is plugged in.

---

### Post by tamoneya on 2008-06-25
run "sudo fdisk -l" again and post the new output.  It also doesnt hurt to post the output of:```
lsusb
```

---

### Post by noah_balboa on 2008-06-25
lsusb:

Bus 007 Device 002: ID 03f0:171d Hewlett-Packard 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 04f2:b023 Chicony Electronics Co., Ltd 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  

fdisk -l:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0e045244

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15368   123443428+   7  HPFS/NTFS
/dev/sda2           18369       19457     8747392+   7  HPFS/NTFS
/dev/sda3           15369       18368    24097500    5  Extended
/dev/sda5           15369       18238    23053243+  83  Linux
/dev/sda6           18239       18368     1044193+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/mmcblk2: 4026 MB, 4026531840 bytes
31 heads, 30 sectors/track, 8456 cylinders
Units = cylinders of 930 * 512 = 476160 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk2p1               9        8457     3928064    b  W95 FAT32

---oops, my SDHC card is in right now. Ignore that.

---

### Post by noah_balboa on 2008-06-26
The external disk is plugged in through USB...doesn't seem to recognize it I guess.

---

### Post by tamoneya on 2008-06-26
can you try a different USB port.  Can you verify that this harddrive works on windows.

---

