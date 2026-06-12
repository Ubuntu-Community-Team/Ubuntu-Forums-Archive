---
title: "Windows backup doesn't boot after ubuntu is installed."
date: 2009-08-07
forum: Installation &amp; Upgrades
---

### Post by Hugh Mulqueen on 2009-08-07
I backed up my windows partition using Nortan Ghost. Then I installed ubuntu 9.04 64bit. and when the installation was complete I rebooted the PC and the entered the Windows entry in grub and the following message was printed on the screen:

NTDLR is missing.
Press (Ctrl+Alt+Del) to restart.

I'm stumped!! I tried the instructions on the following thread but alas no joy.. BOOTLR is missing. Press (Ctrl...yada yada yada....)

[B]This is my boot/grub/menu.lst file:
[/B]
```
title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		6b0e2cf8-04bb-4b90-a274-093cdc128f61
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=6b0e2cf8-04bb-4b90-a274-093cdc128f61 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		6b0e2cf8-04bb-4b90-a274-093cdc128f61
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=6b0e2cf8-04bb-4b90-a274-093cdc128f61 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		6b0e2cf8-04bb-4b90-a274-093cdc128f61
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=6b0e2cf8-04bb-4b90-a274-093cdc128f61 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		6b0e2cf8-04bb-4b90-a274-093cdc128f61
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=6b0e2cf8-04bb-4b90-a274-093cdc128f61 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		6b0e2cf8-04bb-4b90-a274-093cdc128f61
kernel		/boot/memtest86+.bin
quiet

title		Windows XP
root		(hd0,1)
makeactive
chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST
```

**And this is the output of fdisk -l:**

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe7435579

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9671    77682276    7  HPFS/NTFS
/dev/sda2            9672       12082    19366357+  83  Linux
/dev/sda3           12083       30401   147147367+   5  Extended
/dev/sda5           12083       30401   147147336   83  Linux


```

Iam guessing that its something to do with auto-detect OS feature in ubuntu.. Perhaps it deosn't detect recovered partitions? Because I had to manually add the grub entry for windows..

---

### Post by mikewhatever on 2009-08-07
It looks like you added the Grub entry for Windows manually, because the partition numbering is obviously wrong, and the entry is inside the debian kernel list. Why wasn't it detected by the installer? Anyway, the correct partition for Windows would be (hd0,0), change it and try again.

---

### Post by Hugh Mulqueen on 2009-08-08
Thanks, I changed that but the same thing pops up on the screen. 

Any body know what that star (*) denotes on my fdisk -l output?

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   [COLOR="Red"]*[/COLOR]           1        9671    77682276    7  HPFS/NTFS

```

---

### Post by Mark Phelps on 2009-08-08
The "*" means that partition is bootable ...

Mikewhatever indicated the correct menu.lst entry for MS Windows.

It's possible the files got deleted (but unlikely).

You should open your MS Window partition and confirm that NTLDR and the other windows boot files are still there.  You can to that by looking in Places and selecting the icon for the MS Windows partition.  Double-clicking that will open a Nautilus window which you can use to browse the filesystem.

---

