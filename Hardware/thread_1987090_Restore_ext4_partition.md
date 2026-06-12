---
title: "Restore ext4 partition"
date: 2012-05-25
forum: Hardware
---

### Post by Sean Hayes on 2012-05-25
This is regarding my Asus EEE T101MT-EU37-BK laptop, which came with Windows 7 Home Starter and I dual boot with Ubuntu 12.04. While trying to upgrade my memory I had to disable Boot Booster, but the option was missing from my BIOS, so I had to create a new 16MB parittion for the Boot Booster feature, which is where my current issue begins.

To create the 16MB partition, in Windows I ran diskmgmt.msc and I shrunk my Windows partition by 16MB, then I created a new partition with the 16MB of unused space. After creating that new parittion, suddenly the Disk Management program showed the partition where I had Ubuntu installed as free space on an Extended Partition. This wasn't something I did manually, it just happened all by itself.

Now when I boot I get the GRUB rescue prompt. I booted into Ubuntu on a USB drive and inspected the drive with fsck, which confirmed that the partition I had Ubuntu on is now an NTSF extended partition instead of an ext4 Linux partition.

Is there any way to fix the partition and get my data back?

---

### Post by wilee-nilee on 2012-05-25
You might have gone over the 4 primary partition limit and made the HD dynamic, down load the Das-Boot in my sig and extract it to the desktop and run the command and paste the results.txt in a reply.

When you open the reply click on the # in the reply panel and paste the text between the code tags.

```
sudo bash ~/Desktop/bootinfoscript
```

---

### Post by Sean Hayes on 2012-05-25
> **wilee-nilee said:**
> You might have gone over the 4 primary partition limit and made the HD dynamic, down load the Das-Boot in my sig and extract it to the desktop and run the command and paste the results.txt in a reply.

When you open the reply click on the # in the reply panel and paste the text between the code tags.

```
sudo bash ~/Desktop/bootinfoscript
```


```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016 ...........>...r>.......w..V...0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:  Syslinux looks at sector 1444816 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sdb1 starts at sector 
                       0. But according to the info from fdisk, sdb1 starts 
                       at sector 62.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /efi/boot/bootx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   209,684,479   209,682,432   7 NTFS / exFAT / HPFS
/dev/sda2         209,684,480   209,715,199        30,720  ef EFI (FAT-12/16/32)
/dev/sda3         209,719,294   488,396,799   278,677,506   5 Extended
/dev/sda5         480,395,264   488,396,799     8,001,536  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4072 MB, 4072669184 bytes
126 heads, 62 sectors/track, 1018 cylinders, total 7954432 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     7,952,615     7,952,554   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       45d22697-d6d6-4cd0-b026-af3e66086378   ext3       
/dev/sda1        261233AE1233823B                       ntfs       
/dev/sdb1        C0EC-886F                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=auto
	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
/home/ubuntu/Downloads/bootinfoscript-061/bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected

```

---

