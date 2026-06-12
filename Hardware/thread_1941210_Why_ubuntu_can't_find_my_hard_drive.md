---
title: "Why ubuntu can't find my hard drive?"
date: 2012-03-15
forum: Hardware
---

### Post by Marco Virdia on 2012-03-15
I'm trying to  install ubuntu near windows but when i start the  installation i can't go  on because it doesn't find room on the hard  disk. 
  

When i run the installation, from both the cd or USB stick, Ubuntu   checks if there's the internet connection and if there's enough room on   the hard disk. 

Here's the problem: Ubuntu says that there's not enogh room on the hard  disk.
  

On the same hard disk i have Windows and it doesn't give me any   problem. I have all the room that Ubuntu may ask and a lot more,    evidently he can't see my hard disk.
  

I booted the live version of Gparted from CD, i checked the list of   hard drives and i saw that also Gparted doesn't manage to see my hard   disk.
  

I already formatted the whole hard disk, re-installed Windows and  tryed  to install Ubuntu again but i still have the same problem.
  

What can i do to solve this problem?
  

few informations:

1) i used the disk gestion of windows 7 ultimate to format and make partitions
  

2) if i start wubi.exe from windows it opens a dialogue window:     pyrun.exe - disk not present    [a big X image] can not find the hard  drive. Insert a disk into \Device\Harddisk1\DR1    [http://imageshack.us/photo/my-images/259/pyrun.jpg/](http://imageshack.us/photo/my-images/259/pyrun.jpg/)
  

if i press cancel or continue or whatever else it opens a new window   with \harddisk2\DR2, if i close also this new window it goes to   \harddisk3\DR3 and then to hardisk4\DR4
  

3) using the live version of ubuntu from the USB stick i went on the   terminal and told him to check the hard drives: he found only the USB   stick

I booted the boot_info and this is the result:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sde.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdf.

sde1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.01 debian-20100714  ...........>...r>.......(+.4...0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 1427200 of /dev/sde1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sde1 starts at sector 
                       0. But according to the info from fdisk, sde1 starts 
                       at sector 62.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

sdf1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 2011-12-09
    Boot sector info:   Syslinux looks at sector 65544 of /dev/sdf1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sde _____________________________________________________________________

Disk /dev/sde: 1031 MB, 1031798784 bytes
32 heads, 62 sectors/track, 1015 cylinders, total 2015232 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1    *             62     2,013,759     2,013,698   c W95 FAT32 (LBA)


Drive: sdf _____________________________________________________________________

Disk /dev/sdf: 16.0 GB, 16013852672 bytes
78 heads, 14 sectors/track, 28641 cylinders, total 31277056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1    *          8,064    31,277,055    31,268,992   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sde1        3F7D-2B07                              vfat       
/dev/sdf1        860E-3118                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sde1        /cdrom                   vfat        (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdf1        /media/PENDRIVE          vfat        (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr0         /media/Ubuntu 10.10 amd64 iso9660     (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)


=========================== sde1/boot/grub/grub.cfg: ===========================

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
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sde1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sde1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sde1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sde1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=========================== sdf1/boot/grub/grub.cfg: ===========================

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
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdf1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option  to install or run from USB at startup, remove # from the following  line. This line was commented out (by request of many) to allow the old  menu to be presented and to enable booting straight into the Live  Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdf1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdf1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdf1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

sda sdb sdc sdd no block devices found 

=============================== StdErr Messages: ===============================

boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected
boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

Someone knows how to help me or knows someone who can do it?

---

### Post by javierc on 2012-03-15
its a wild guess but are you encrypting your hard drive with windows 7 ultimate? probably thats not the problem

but you should at least provide details like how much disk space you have left for ubuntu. You say plenty but i rather understands details that vague words.

---

### Post by oldfred on 2012-03-15
The boot script you ran only shows the 1GB & 16GB flash drives. Where is the hard drive?

Have you created more than the allowed 4 primary partitions and Windows converted to dynamic partitions. Linux does not work with dynamic partitions or are you running some Windows RAID or other special device?

---

### Post by Marco Virdia on 2012-03-16
This is the formatting of the main hard drive:

[IMG]http://i.imgur.com/129Aj.jpg[/IMG]


The layout is Simple and the Type is Basic.
Boot_info doesn't show my main hard drive because ubuntu can't see it (i posted the boot_info to show you that ubuntu can't see the hard drive in question)
I'm not running any Windows RAID nor any other special device.
Where can the problem be? 
I must find a solution to this problem because i really need it for work. :(

---

### Post by oldfred on 2012-03-16
Try running chkdsk on your c: drive in Windows. If errors you have to rerun until no errors.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

A while back I had a similar issue, but have not seen anyone recently have something similar and assumed some things were fixed. Normally if the NTFS partition needs chkdsk it mounts it with an error message.

My old XP install booted, but gparted took forever to load and only showed my other drives. I then ran chkdsk on XP. XP then booted a bit fasted and gparted immediately showed it.

Also use the Windows tools to shrink the Windows partition but not to create new partitions. Make a Windows repairCD/USB also.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

You never can have enough backups:
The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by Marco Virdia on 2012-03-16
i ran the chkdsk on windows and this is the result:

[IMG]http://i.imgur.com/oncLH.jpg[/IMG]


i also shrinked the partition in orther to have that amount of unallocated space

[IMG]http://i.imgur.com/iLzm7.jpg[/IMG]


then i tryed to boot the ubuntu isntallation from CD  but once again this was the result:


[IMG]http://i.imgur.com/RkYPT.png[/IMG]


ubuntu can't see the main hard disk, but he can see my USB stick when i plug it

---

### Post by oldfred on 2012-03-16
What are your BIOS settings?

This is a list of issues others have had. Most may not apply:

BIOS in not updated to latest revision
BIOS not set to boot CD or USB first
BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA 6 Gbit/s  from 6 Gbs to a SATA II - 3Gbs 
BIOS & disable "Boot Sector Virus Protection"
Other BIOS settings - Security or locked down Boot sector, Bitlocker
core unlocker feature on asus m4a87td usb3 was causing the problem
Old BIOS, new drive 137GB max boot size
NTFS partition needs chkdsk, gparted will not see drive if chkdsk flag set, flag is set on resize
Raid meta data on drive - even if one drive (Vendor happend to set it on)
Old gpt data on drive
Disable Quickboot in BIOS
BIOS setting, Keyboard response in grub really slow
Fast Boot setting prevents keyboard from working & other issues
The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Sometimes specific issues by motherboard like this:
[Natty] Marvell 88SE9120 IDE-Part not working 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/777325](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/777325)
External drive needed separate power supply

In the Asus BIOS I selected Advanced Mode>Advanced>SATA Configuration.
Changed IDE Mode to AHCI Mode
Then,when the SATA3G_1 selection appears in the drive list below,select the Enabled option.

It was in the BIOS. Under Onboard Devices Settings, the SATA Mode was set to SATA. I changed it to AHCI. Then another line showed up in the BIOS that stated "Change the AHCI DID for Linux to Enabled. I booted to win7 and it loaded some new drivers. I booted to Gpart and glory be there were my hard drives.

Change SATA controller mode from AHCI to Compatibility (AHCI should be ok for Vista/7 & Linux), XP may not have AHCI driver.
[http://ubuntuforums.org/showthread.php?t=1694750&page=8](http://ubuntuforums.org/showthread.php?t=1694750&page=8) post #79
Standard BIOS Settings -> [drive you want to change] -> IDE Access -> “Large”, did the trick. 

SATA mode should stay in AHCI unless you are getting nasty issues (which shouldn't happen with linux or vista/win7). The main reason why people change SATA mode to 'compatibility' is because winXP wont work with AHCI without loading the drivers..and you need a floppy drive to load the drivers, which most newer computers don't have (and lots of people are lazy anyway).

Oldfred was right on, it was the SATA Native IDE setting that hosed Grub. I had to set the OnChip SATA Type to AHCI in order to boot using Grub. As for the OnChip SATA Port 4/5 Type setting it doesn't have any affect on Grub, it can be set to IDE or as SATA Type. My MB BIOS doesn't have a Compatibility or LBA setting so I have to find the AHCI XP drivers if I want to Multi-Boot XP and Ubuntu.

HOWTO: enable AHCI mode after installing Windows 
However, in the real world the performance difference isn't huge.
[http://forums.pcper.com/showthread.php?t=444831](http://forums.pcper.com/showthread.php?t=444831)
Google search on xp  - ahci after install
Early SATA chips do not support SATA 3 Gbit/s.
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)

---

### Post by Marco Virdia on 2012-03-19
Thanks a lot man, i changed to ACHI mode from IDE mode and finally ubuntu found my hard drive! :p

---

