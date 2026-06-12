---
title: "Problem switching from Vista+XP to Ubuntu+XP"
date: 2009-09-09
forum: Installation &amp; Upgrades
---

### Post by kaoD on 2009-09-09
Hello. I have a very strange problem. I used to have a dual boot with Windows XP and Vista, but I decided to remove Vista and switch to dual XP+Ubuntu. I installed Ubuntu, formatting Vista's partition in the process, and installing Ubuntu over it. No problem at all. GRUB was correctly installed and I could dual boot, but I had a little drawback: GRUB kept Vista's bootloader in the list, and I wanted XP's bootloader, so I decided to reinstall XP's bootloader with the install CD, and then reinstall Ubuntu.

I had some problems installing WinXP because my SATA driver's aren't included in XP's install CD and I have no floppy drive, so I switched my BIOS to IDE Compatibility mode (I suppose it emulates IDE), letting the XP install CD restore XP's bootloader without SATA drivers. It worked, I rebooted, XP started fine and switching back to AHCI didn't break anything, so I just had to reinstall GRUB and everything would be fine... but it didn't go well. Now, when I try to reinstall Ubuntu using the LiveCD, during the installation my drive is shown as if it were completely blank (Without any format), but XP is fine with the partitioning. GParted shows the same problem, 931.00 unallocated GB... but surprisingly I can mount and even browse those partitions! fdisk lists my partitiones fine too:
```
ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4f7b4f7a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      106411   854746326    7  HPFS/NTFS
/dev/sda2          106412      121601   122013675    5  Extended
/dev/sda3          121353      121601     2000092+  82  Linux swap / Solaris
/dev/sda5          106413      121351   119997486   83  Linux

# This is an old ATA drive
Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x49664965

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14594   117218712   42  SFS
```
(Weird partition numbering anyways...)

I tried reinstalling GRUB from the LiveCD, but it didn¡t work either:
```
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,5)
grub> root (hd0,5)
root (hd0,5)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,5)/boot/grub/stage2 /boot/grub/menu.lst"... failed

Error 22: No such partition
```

Is there any way to fix this, or I am stuck with WIndowsXP forever?
Thank you :)

---

### Post by presence1960 on 2009-09-09
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

