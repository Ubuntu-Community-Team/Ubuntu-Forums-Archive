---
title: "Invalid or Damaged Bootable Partition after HDD Upgrade"
date: 2008-02-27
forum: Hardware &amp; Laptops
---

### Post by davidbarton on 2008-02-27
I have upgraded (replaced) the HDD in my Dell Latitude D820 with a new Seagate Momentus 200G.  I am running Ubuntu 7.10 Gutsy.

To do this, I created a partition structure, copied over the files, and installed grub on the new drive.  After much messing around, I believe I was able to get it to boot but didn't check for repeatability.

I have now tried to reboot, and the system is returning the error "Invalid or damaged bootable partition".  This appears to occur before grub even loads.

I have tried reinstalling grub to no avail.  The grub install runs, see output below, but I get the same error message.

I can boot using my old HDD in a USB case.  The machine boots from USB and goes into the grub selection, where I have a custom entry in menu.lst that uses the new drive.  I detach the old disk from USB, select the custom menu item and boot up.  This lets me use my new disk as normal, but I cannot boot without the old one plugged in.  So the new disk does not *appear* to be corrupt, unless it's just the MBR.

Can anyone please help me get my machine booting like normal.

Thanks.

David


======== GRUB REINSTALL ============
find /boot/grub/menu.lst
 (hd0,0)

setup (hd0) (hd0,0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded



======= GRUB CONFIG ==========
My /boot/grub/menu.lst is attached

#ls -l /boot/grub/
total 188
-rw-r--r-- 1 root root    197 2006-05-05 22:09 default
-rw-r--r-- 1 root root      0 2008-02-24 12:19 device.map
-rw-r--r-- 1 root root   7508 2006-05-05 22:09 e2fs_stage1_5
-rw-r--r-- 1 root root   7332 2006-05-05 22:09 fat_stage1_5
-rw-r--r-- 1 root root   8128 2006-05-05 22:09 jfs_stage1_5
-rw-r--r-- 1 root root   5506 2008-02-27 17:30 menu.lst
-rw-r--r-- 1 root root   5506 2008-02-27 16:11 menu.lst~
-rw-r--r-- 1 root root   6804 2006-05-05 22:09 minix_stage1_5
-rw-r--r-- 1 root root   9076 2006-05-05 22:09 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2006-05-05 22:09 stage1
-rw-r--r-- 1 root root 105428 2006-05-05 22:09 stage2
-rw-r--r-- 1 root root   8764 2006-05-05 22:09 xfs_stage1_5


======== DISK INFO ============
#fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008354d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3259    26177886   83  Linux
/dev/sda2            3260       24321   169180515    5  Extended
/dev/sda5            3260        3514     2048256   83  Linux
/dev/sda6            3515        3769     2048256   82  Linux swap / Solaris
/dev/sda7            3770       24321   165083908+  83  Linux

Disk /dev/sdb: 515 MB, 515899392 bytes
16 heads, 32 sectors/track, 1968 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0xbb5009ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1968      503792    e  W95 FAT16 (LBA)


#blkid
/dev/sda6: TYPE="swap" UUID="103146a3-8cd8-4499-8882-aaa848de1d88"
/dev/sdb1: SEC_TYPE="msdos" LABEL="KINGSTON" UUID="D34F-5F04" TYPE="vfat"
/dev/sda1: UUID="b810c78b-67f0-4642-8e52-2f03817ce2b5" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda5: UUID="4ac1283d-c7b2-4709-ae04-391185d91a1b" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda7: UUID="827f7432-c15f-41d1-9179-3a5b0ab53a29" TYPE="crypt_LUKS"
/dev/mapper/enchome: UUID="be16f054-8cd5-4fa5-8647-b463fa647ad8" SEC_TYPE="ext2" TYPE="ext3"



============= RAW MBR DATA =============
I tried dumping my MBR.  The first few lines are below:

dd if=/dev/sda of=mbr.bin bs=512 count=1
od -xa mbr.bin
0000000 48eb 1090 d08e 00bc b8b0 0000 d88e c08e
          k   H dle dle  so   P   < nul   0   8 nul nul  so   X  so   @
0000020 befb 7c00 00bf b906 0200 a4f3 21ea 0006
          {   > nul   |   ? nul ack   9 nul stx   s   $   j   ! ack nul
0000040 be00 07be 0438 0b75 c683 8110 fefe 7507
        nul   >   > bel   8 eot   u  vt etx   F dle soh   ~   ~ bel   u
0000060 ebf3 b416 b002 bb01 7c00 80b2 748a 0203
          s   k syn   4 stx   0 soh   ; nul   |   2 nul  nl   t etx stx


This is different from what is in grub:
od -xa  /boot/grub/stage1 | head -n 6
0000000 48eb 0090 0000 0000 0000 0000 0000 0000
          k   H dle nul nul nul nul nul nul nul nul nul nul nul nul nul
0000020 0000 0000 0000 0000 0000 0000 0000 0000
        nul nul nul nul nul nul nul nul nul nul nul nul nul nul nul nul

Also slightly different from what is on my old disk's MBR (48eb are the first 2 bytes)

---

### Post by chrisdeckard on 2008-02-28
Most likely you didn't reload GRUB to the MBR of the new disk.  You need to run grub-install to have it load into the MBR.

-Chris

---

