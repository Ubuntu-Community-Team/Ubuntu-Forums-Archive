---
title: "Grub error 15, UUID mismatch?"
date: 2009-06-29
forum: Installation &amp; Upgrades
---

### Post by quantumstitch on 2009-06-29
Hi all,
I recently added a 300GB drive to my ubuntu box. I did a fresh install of 9.04 on that disk and everything has worked just fine. After applying new kernel updates when I reboot I get a grub error (#15). I can bypass this by selecting the 300GB drive from the boot menu. This allows the machine to boot into Ubuntu, no problem. I am pretty sure that it has the boot flag on it and I removed it from the old drive (it's still in the machine and has lots of data on it). The machine is running headless and it's a pain in the butt, to plug a display in every time I need to reboot.

Here's some info to help.

fdisk -l

```
Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3737be1e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13177   105844221    7  HPFS/NTFS
/dev/sda2           13178       36481   187189380    5  Extended
/dev/sda5           13178       35531   179558473+  83  Linux
/dev/sda6           35532       36481     7630843+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000327a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00065741

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       58569   470455461   83  Linux
```

blkid

```
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="36883566883525B1" TYPE="ntfs" 
/dev/sda5: UUID="7736b6b2-baed-4d54-a65b-21f1a53c7e6e" TYPE="ext3" 
/dev/sda6: UUID="e09160be-e9ed-4a5f-baeb-037b56b6376f" TYPE="swap"
```

more /etc/fstab

```
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="36883566883525B1" TYPE="ntfs" 
/dev/sda5: UUID="7736b6b2-baed-4d54-a65b-21f1a53c7e6e" TYPE="ext3" 
/dev/sda6: UUID="e09160be-e9ed-4a5f-baeb-037b56b6376f" TYPE="swap"
```

---

### Post by merlinus on 2009-06-29
Compare the UUIDs with those in /boot/grub/menu.lst.

Also, linux does not need boot flags like windows.

---

### Post by louieb on 2009-06-29
Just a note about blikid it has a bug where its cache is not getting updated.
to get around it tell it to bypass the cache.
```
sudo blkid -c /dev/null  
```

Don't think **uuid** is the problem but the way grub uses boot order to determine which drive is (hd0).

Also just wondering can you go into BIOS and changed the boot order of your hard drives permanently?

If not then boot a live CD and open a terminal window
```
sudo grub
```

at the **grub>** prompt

```
find /boot/grub/stage2
```
will return something like (hd#,#)
now modify the MBR of (hd0)

```
root (hd#,#)
setup (hd0)
quit
```

Should work - let us know.

---

### Post by Rowan_ on 2009-11-17
Changing the Boot sequence in the Bios worked for me.  
Thanks, no more error 15 when Grub tries to load.

---

