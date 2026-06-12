---
title: "Grub fails after upgrade to 64bit Jaunty"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by keepitsimpleengr on 2009-05-02
I could use some help in figuring this out......

I upgraded my amd64 workstation from 8.10 to 9.04 using the alternative CD off-line.  Several errors occurred (Launchpad 366795, 366962) and after the upgrade 9.04 failed to operate properly.

While trying to fix the upgraded system, hardware failures occurred resulting in the replacement of the mainboard and power supply, and the removal of a video adapter card which was half of a SLI installation.

After replacing the hardware the Windows systems were updated but the 9.04 failed to boot in GRUB.  Before the hardware replacement, 9.04 would boot but not operate properly.

When booting the Ubuntu partition, the following would occur...

"GRUB Loading stage1.5¬
"¬
"GRUB loading, please wait...¬
"Error 17   "

It is my understanding that this error indicates GRUB cannot find a file, or it's partition.

I ran LiveCD and discovered that the UUIDs all match for the Ubunto partition (see attachment)

Note: OEL/RHEL boots from GRUB and uses LVM.  Ubuntu shares swap space with it on a high speed disk.
The 32bit Ubuntu 9.04 upgrade on a legacy workstation worked great.

---

### Post by keepitsimpleengr on 2009-05-03
So I decide to verify that 64bit 9.04 upgrade can read the boot partition.

I have created the device.map from the LiveCD and saved it to the /boot directory of the 9.04 root partition, see attached.

So now I mount the root partition of 9.04, change it to root to run GRUB from there.  The device map it creates does not contain any hard drives, only the floppy drive, (fd0).

This explains how grub has failed to boot 9.04 even though device.map in /boot/grub is correct.

Any help here…?

---

### Post by caljohnsmith on 2009-05-03
I think it would help to first get a clearer picture of your setup related to your booting problem, so how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

John

---

### Post by keepitsimpleengr on 2009-05-04
> **caljohnsmith said:**
> ```
sudo bash ~/Desktop/boot_info_script*.sh
```
John

John...

Thanks for the reply.

Before reading your reply, I had done the following:

Booted LiveCD, mounted disk with the 9.04 system (hd3), ran from GRUB "setup (hd3)"

The result was when I booted from (hd3) I got the GRUB screen produced from menu.lst.  But when I tried to boot 9.04 (or OEL/RHEL,WinXP,Vista) from this screen, I got another Error 17, could not find partition.  Before running setup (hd3), I would get "GRUB Loading stage1.5¬,¬GRUB loading, please wait...¬"Error 17 ".

I ran the script *boot_info_script032.sh* from LiveCD, as shown below.  I also mounted the 9.04 partition from LiveCD, changed root to it and attempted to run the script.  It failed due to permission error on "/dev/null".  When I create a device.map from the same mounted directory for the 9.04 root, I get only (fd0), no hard drives.

Here is RESULTS.txt…

```
============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #4 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc
 => Grub0.97 is installed in the MBR of /dev/sdd and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sde
 => Windows is installed in the MBR of /dev/sdf

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/grub.conf

sdb2: _________________________________________________________________________

    File system:       lvm2pv
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'lvm2pv'

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdd1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdd3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdd5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdd6: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       lvm2pv
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'lvm2pv'

sde2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sde5: _________________________________________________________________________

    File system:       lvm2pv
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'lvm2pv'

sdf1: _________________________________________________________________________

    File system:       lvm2pv
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'lvm2pv'

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4ff3fbd8

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   293,025,599   293,025,537   7 HPFS/NTFS
/dev/sda2         293,025,600   488,392,064   195,366,465   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5d1435a2

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63       208,844       208,782  83 Linux
/dev/sdb2             208,845   293,041,664   292,832,820  8e Linux LVM


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x99a0e472

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   284,350,499   284,350,437   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0002bc91

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63   537,181,469   537,181,407  83 Linux
/dev/sdd3         537,181,470   976,768,064   439,586,595   5 Extended
/dev/sdd5         537,181,533   822,399,479   285,217,947   7 HPFS/NTFS
/dev/sdd6         822,399,543   976,768,064   154,368,522  83 Linux


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00025f19

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *             63   244,123,739   244,123,677  83 Linux
/dev/sde2         244,123,740   976,768,064   732,644,325   5 Extended
/dev/sde5         244,123,803   976,768,064   732,644,262   7 HPFS/NTFS


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x01339c1f

Partition  Boot         Start           End          Size  Id System

/dev/sdf1    *             63   244,123,739   244,123,677  93 Amoeba/Accidently Hidden Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="30D8EF5AD8EF1CBA" LABEL="C_WINXP" TYPE="ntfs" 
/dev/sda2: UUID="502E5E672E5E45DE" LABEL="KISE-005.250GB.P2.NTFS" TYPE="ntfs" 
/dev/sdb1: LABEL="/boot" UUID="0abcb589-d896-46f2-8add-020c88f20c7b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: UUID="3t8u97-WW04-Pn3s-QsMz-kGRH-gqI5-PJ3Bi8" TYPE="lvm2pv" 
/dev/sdc1: UUID="D602FFF702FFDB07" LABEL="C_VISTA" TYPE="ntfs" 
/dev/sdd1: LABEL="500GB.1.P1" UUID="3ad2f993-cd06-4982-a4e0-1db8f3fc4a26" TYPE="ext3" 
/dev/sdd5: UUID="34E494389D825B84" LABEL="500GB.1.P2.NTFS.VISTA" TYPE="ntfs" 
/dev/sdd6: LABEL="500GB.1.EXT3.P3" UUID="3756dc20-9877-1b72-76bc-3cd55121804c" TYPE="ext2" 
/dev/sde1: UUID="ls7JTT-U4kS-v3kw-vNpi-3BxX-sY8Q-mrmmXy" TYPE="lvm2pv" 
/dev/sde5: UUID="tq8JAo-b3Q9-QEkm-z5VS-9tNQ-xr0B-mTGGG7" TYPE="lvm2pv" 
/dev/sdf1: UUID="08AIUO-3MpY-KBIr-gq4s-U4Eu-14Pn-Rcblf0" TYPE="lvm2pv" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdd1 on /media/500GB.1.P1 type ext3 (rw,nosuid,nodev,uhelper=hal)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=8
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows Debug" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="SAFE MODE" /noexecute=optin /fastdetect

============================= sdb1/grub/grub.conf: =============================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,0)
#          kernel /vmlinuz-version ro root=/dev/VolGroup00/LogVol00
#          initrd /initrd-version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd1,0)/grub/splash.xpm.gz
hiddenmenu
title Enterprise Linux Enterprise Linux AS (2.6.9-67.0.22.0.1.ELsmp)
	root (hd1,0)
        kernel /vmlinuz-2.6.9-67.0.22.0.1.ELsmp ro root=/dev/VolGroup00/LogVol00 rhgb quiet
	initrd /initrd-2.6.9-67.0.22.0.1.ELsmp.img
title Enterprise Linux Enterprise Linux AS (2.6.9-67.0.22.0.1.EL)
	root (hd1,0)
        kernel /vmlinuz-2.6.9-67.0.22.0.1.EL ro root=/dev/VolGroup00/LogVol00 rhgb quiet
	initrd /initrd-2.6.9-67.0.22.0.1.EL.img
title Enterprise Linux Enterprise Linux AS (2.6.9-67.0.20.0.2.ELsmp)
	root (hd1,0)
        kernel /vmlinuz-2.6.9-67.0.20.0.2.ELsmp ro root=/dev/VolGroup00/LogVol00 rhgb quiet
	initrd /initrd-2.6.9-67.0.20.0.2.ELsmp.img
title Enterprise Linux Enterprise Linux AS (2.6.9-67.0.20.0.2.EL)
	root (hd1,0)
        kernel /vmlinuz-2.6.9-67.0.20.0.2.EL ro root=/dev/VolGroup00/LogVol00 rhgb quiet
	initrd /initrd-2.6.9-67.0.20.0.2.EL.img
title Enterprise Linux Enterprise Linux AS (2.6.9-55.0.16.0.1.ELsmp)
	root (hd1,0)
        kernel /vmlinuz-2.6.9-55.0.16.0.1.ELsmp ro root=/dev/VolGroup00/LogVol00 rhgb quiet
	initrd /initrd-2.6.9-55.0.16.0.1.ELsmp.img
title Enterprise Linux Enterprise Linux AS (2.6.9-67.0.7.0.1.ELsmp)
	root (hd1,0)
        kernel /vmlinuz-2.6.9-67.0.7.0.1.ELsmp ro root=/dev/VolGroup00/LogVol00 rhgb quiet
	initrd /initrd-2.6.9-67.0.7.0.1.ELsmp.img
title Enterprise Linux Enterprise Linux AS (2.6.9-67.0.7.0.1.EL)
	root (hd1,0)
        kernel /vmlinuz-2.6.9-67.0.7.0.1.EL ro root=/dev/VolGroup00/LogVol00 rhgb quiet
	initrd /initrd-2.6.9-67.0.7.0.1.EL.img
title Enterprise Linux Enterprise Linux AS (2.6.9-67.0.4.0.1.ELsmp)
	root (hd1,0)
        kernel /vmlinuz-2.6.9-67.0.4.0.1.ELsmp ro root=/dev/VolGroup00/LogVol00 rhgb quiet
	initrd /initrd-2.6.9-67.0.4.0.1.ELsmp.img
title Enterprise Linux Enterprise Linux AS (2.6.9-67.0.4.0.1.EL)
	root (hd1,0)
	kernel /vmlinuz-2.6.9-67.0.4.0.1.EL ro root=/dev/VolGroup00/LogVol00 rhgb quiet
	initrd /initrd-2.6.9-67.0.4.0.1.EL.img
title Enterprise Linux Enterprise Linux AS (2.6.9-67.0.1.0.1.ELsmp)
	root (hd1,0)
	kernel /vmlinuz-2.6.9-67.0.1.0.1.ELsmp ro root=/dev/VolGroup00/LogVol00 rhgb quiet
	initrd /initrd-2.6.9-67.0.1.0.1.ELsmp.img
title Enterprise Linux Enterprise Linux AS (2.6.9-67.0.1.0.1.EL)
	root (hd1,0)
	kernel /vmlinuz-2.6.9-67.0.1.0.1.EL ro root=/dev/VolGroup00/LogVol00 rhgb quiet
	initrd /initrd-2.6.9-67.0.1.0.1.EL.img
title Enterprise Linux Enterprise Linux AS (2.6.9-67.0.0.0.1.EL)
	root (hd1,0)
	kernel /vmlinuz-2.6.9-67.0.0.0.1.EL ro root=/dev/VolGroup00/LogVol00 rhgb quiet
	initrd /initrd-2.6.9-67.0.0.0.1.EL.img
title Enterprise Linux Enterprise Linux AS (2.6.9-67.0.0.0.1.ELsmp)
	root (hd1,0)
	kernel /vmlinuz-2.6.9-67.0.0.0.1.ELsmp ro root=/dev/VolGroup00/LogVol00 rhgb quiet
	initrd /initrd-2.6.9-67.0.0.0.1.ELsmp.img
title Enterprise Linux Enterprise Linux AS (2.6.9-55.0.12.0.1.ELsmp)
	root (hd1,0)
	kernel /vmlinuz-2.6.9-55.0.12.0.1.ELsmp ro root=/dev/VolGroup00/LogVol00 rhgb quiet
	initrd /initrd-2.6.9-55.0.12.0.1.ELsmp.img
title Enterprise Linux Enterprise Linux AS (2.6.9-55.0.12.0.1.EL)
	root (hd1,0)
	kernel /vmlinuz-2.6.9-55.0.12.0.1.EL ro root=/dev/VolGroup00/LogVol00 rhgb quiet
	initrd /initrd-2.6.9-55.0.12.0.1.EL.img
title Enterprise Linux Enterprise Linux AS (2.6.9-55.0.9.0.1.ELsmp)
	root (hd1,0)
	kernel /vmlinuz-2.6.9-55.0.9.0.1.ELsmp ro root=/dev/VolGroup00/LogVol00 rhgb quiet
	initrd /initrd-2.6.9-55.0.9.0.1.ELsmp.img
title Enterprise Linux Enterprise Linux AS (2.6.9-55.0.9.0.1.EL)
	root (hd1,0)
	kernel /vmlinuz-2.6.9-55.0.9.0.1.EL ro root=/dev/VolGroup00/LogVol00 rhgb quiet
	initrd /initrd-2.6.9-55.0.9.0.1.EL.img
title Enterprise Linux Enterprise Linux AS (2.6.9-55.0.6.0.1.ELsmp)
	root (hd1,0)
	kernel /vmlinuz-2.6.9-55.0.6.0.1.ELsmp ro root=/dev/VolGroup00/LogVol00 rhgb quiet
	initrd /initrd-2.6.9-55.0.6.0.1.ELsmp.img
title Enterprise Linux Enterprise Linux AS (2.6.9-55.0.6.0.1.EL)
	root (hd1,0)
	kernel /vmlinuz-2.6.9-55.0.6.0.1.EL ro root=/dev/VolGroup00/LogVol00 rhgb quiet
	initrd /initrd-2.6.9-55.0.6.0.1.EL.img
title Enterprise (2.6.9-55.0.0.0.2.ELsmp)
	root (hd1,0)
	kernel /vmlinuz-2.6.9-55.0.0.0.2.ELsmp ro root=/dev/VolGroup00/LogVol00 rhgb quiet
	initrd /initrd-2.6.9-55.0.0.0.2.ELsmp.img
title Enterprise-up (2.6.9-55.0.0.0.2.EL)
	root (hd1,0)
	kernel /vmlinuz-2.6.9-55.0.0.0.2.EL ro root=/dev/VolGroup00/LogVol00 rhgb quiet
	initrd /initrd-2.6.9-55.0.0.0.2.EL.img
title Other
	rootnoverify (hd2,0)
	chainloader +1

=================== sdb1: Location of files loaded by Grub: ===================


    .1GB: grub/grub.conf
    .1GB: grub/menu.lst
    .0GB: grub/stage2
    .0GB: initrd-2.6.9-55.0.0.0.2.EL.img
    .0GB: initrd-2.6.9-55.0.0.0.2.ELsmp.img
    .0GB: initrd-2.6.9-55.0.12.0.1.EL.img
    .0GB: initrd-2.6.9-55.0.12.0.1.ELsmp.img
    .0GB: initrd-2.6.9-55.0.16.0.1.ELsmp.img
    .0GB: initrd-2.6.9-55.0.6.0.1.EL.img
    .0GB: initrd-2.6.9-55.0.6.0.1.ELsmp.img
    .0GB: initrd-2.6.9-55.0.9.0.1.EL.img
    .0GB: initrd-2.6.9-55.0.9.0.1.ELsmp.img
    .0GB: initrd-2.6.9-67.0.0.0.1.EL.img
    .0GB: initrd-2.6.9-67.0.0.0.1.ELsmp.img
    .0GB: initrd-2.6.9-67.0.1.0.1.EL.img
    .0GB: initrd-2.6.9-67.0.1.0.1.ELsmp.img
    .0GB: initrd-2.6.9-67.0.20.0.2.EL.img
    .0GB: initrd-2.6.9-67.0.20.0.2.ELsmp.img
    .0GB: initrd-2.6.9-67.0.22.0.1.EL.img
    .1GB: initrd-2.6.9-67.0.22.0.1.ELsmp.img
    .0GB: initrd-2.6.9-67.0.4.0.1.EL.img
    .0GB: initrd-2.6.9-67.0.4.0.1.ELsmp.img
    .0GB: initrd-2.6.9-67.0.7.0.1.EL.img
    .0GB: initrd-2.6.9-67.0.7.0.1.ELsmp.img
    .0GB: initrd.backup
    .0GB: vmlinuz-2.6.9-55.0.0.0.2.EL
    .0GB: vmlinuz-2.6.9-55.0.0.0.2.ELsmp
    .0GB: vmlinuz-2.6.9-55.0.12.0.1.EL
    .0GB: vmlinuz-2.6.9-55.0.12.0.1.ELsmp
    .0GB: vmlinuz-2.6.9-55.0.16.0.1.ELsmp
    .0GB: vmlinuz-2.6.9-55.0.6.0.1.EL
    .0GB: vmlinuz-2.6.9-55.0.6.0.1.ELsmp
    .0GB: vmlinuz-2.6.9-55.0.9.0.1.EL
    .0GB: vmlinuz-2.6.9-55.0.9.0.1.ELsmp
    .0GB: vmlinuz-2.6.9-67.0.0.0.1.EL
    .0GB: vmlinuz-2.6.9-67.0.0.0.1.ELsmp
    .0GB: vmlinuz-2.6.9-67.0.1.0.1.EL
    .0GB: vmlinuz-2.6.9-67.0.1.0.1.ELsmp
    .0GB: vmlinuz-2.6.9-67.0.20.0.2.EL
    .0GB: vmlinuz-2.6.9-67.0.20.0.2.ELsmp
    .0GB: vmlinuz-2.6.9-67.0.22.0.1.EL
    .1GB: vmlinuz-2.6.9-67.0.22.0.1.ELsmp
    .0GB: vmlinuz-2.6.9-67.0.4.0.1.EL
    .0GB: vmlinuz-2.6.9-67.0.4.0.1.ELsmp
    .0GB: vmlinuz-2.6.9-67.0.7.0.1.EL
    .0GB: vmlinuz-2.6.9-67.0.7.0.1.ELsmp

=========================== sdd1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default   0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout   10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title   Windows 95/98/NT/2000
# root    (hd0,0)
# makeactive
# chainloader +1
#
# title   Linux
# root    (hd0,1)
# kernel  /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=3ad2f993-cd06-4982-a4e0-1db8f3fc4a26 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd3,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash vga=796

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=3

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=3ad2f993-cd06-4982-a4e0-1db8f3fc4a26 video=vesafb:ywrap,mtrr vga=0x31A crashkernel=128M@16M 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=3ad2f993-cd06-4982-a4e0-1db8f3fc4a26 ro single  
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-14-generic
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=3ad2f993-cd06-4982-a4e0-1db8f3fc4a26 ro splash vga=796 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=3ad2f993-cd06-4982-a4e0-1db8f3fc4a26 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 9.04, kernel 2.6.24-21-generic
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=3ad2f993-cd06-4982-a4e0-1db8f3fc4a26 ro splash vga=796 
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 9.04, kernel 2.6.24-21-generic (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=3ad2f993-cd06-4982-a4e0-1db8f3fc4a26 ro  single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 9.04, memtest86+
root		(hd3,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
# video=vesafb:ywrap,mtrr vga=0x31A crashkernel=128M@16M
title   Other operating systems:
root

title OEL4.5 Enterprise Linux AS (2.6.9-67.0.22.0.1.ELsmp)
  root (hd1,0)
        kernel /vmlinuz-2.6.9-67.0.22.0.1.ELsmp ro root=/dev/VolGroup00/LogVol00 video=vesafb:ywrap,mtrr vga=0x31A crashkernel=128M@16M
  initrd /initrd-2.6.9-67.0.22.0.1.ELsmp.img

#title OEL5.1 (2.6.18-53.el5)
# root (hd2,0)
# kernel /vmlinuz-2.6.18-53.1.14.0.1.el5 ro root=/dev/VolGroup51/LogVolume51 video=vesafb:ywrap,mtrr vga=0x31A crashkernel=128M@16M
# initrd /initrd-2.6.18-53.1.14.0.1.el5.img


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title   Windows XP Professional x64 Edition
root    (hd0,0)
savedefault
makeactive
#map   (hd0) (hd1)
#map   (hd1) (hd0)
chainloader +1

title   Vista Ultimate x64 Edition
root    (hd2,0)
savedefault
makeactive
map   (hd0) (hd2)
map   (hd2) (hd0)
chainloader +1

=============================== sdd1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdd1
UUID=3ad2f993-cd06-4982-a4e0-1db8f3fc4a26 /               ext3    relatime,errors=remount-ro 0       1
/dev/VolGroup00/LogVol01  swap          swap    pri=4           0 0
/dev/VolGroup51/LogVolSwap swap         swap    pri=4           0 0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdd1: Location of files loaded by Grub: ===================


 116.0GB: boot/grub/menu.lst
 115.9GB: boot/grub/stage2
 116.1GB: boot/initrd.img-2.6.24-21-generic
 116.1GB: boot/initrd.img-2.6.24-21-generic.bak
 116.0GB: boot/initrd.img-2.6.27-14-generic
 115.9GB: boot/initrd.img-2.6.28-11-generic
 116.0GB: boot/vmlinuz-2.6.24-21-generic
 116.0GB: boot/vmlinuz-2.6.27-14-generic
 116.0GB: boot/vmlinuz-2.6.28-11-generic
 115.9GB: initrd.img
 116.0GB: initrd.img.old
 116.0GB: vmlinuz
 116.0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  e8 12 01 b9 f0 01 be 10  7c bf 10 06 57 f3 a4 c3  |........|...W...|
00000010  8b 4e 14 83 f9 0e 75 08  8d 5e 07 43 02 07 e2 fb  |.N....u..^.C....|
00000020  8c 56 0c 8c 56 0e 75 69  8a 56 10 84 d2 79 62 e8  |.V..V.ui.V...yb.|
00000030  f6 00 bb aa 55 cd 13 72  6f 3b 5e 5c 75 6a d1 e9  |....U..ro;^\uj..|
00000040  73 66 b4 42 c6 46 02 01  eb 66 89 b6 f6 fe 8a 44  |sf.B.F...f.....D|
00000050  04 84 c0 74 0f 3c 05 74  0b 3c 0f 74 07 8a 14 80  |...t.<.t.<.t....|
00000060  e2 80 75 cb 83 c6 10 06  c4 5c 08 89 5e 08 8c 46  |..u......\..^..F|
00000070  0a 07 fe 8e f9 fe 75 d2  b0 31 c6 46 d7 50 88 46  |......u..1.F.P.F|
00000080  d4 be 6a 07 ac 84 c0 74  08 b4 0e b3 07 cd 10 eb  |..j....t........|
00000090  f3 e8 81 00 88 46 11 be  ae 07 3c 05 75 c6 cd 16  |.....F....<.u...|
000000a0  33 d2 89 56 08 89 56 0a  e8 7d 00 72 1b b8 01 02  |3..V..V..}.r....|
000000b0  bf 05 00 8b dc 56 50 50  32 e4 cd 13 58 8b f5 cd  |.....VPP2...X...|
000000c0  13 58 5e 73 03 4f 75 eb  b0 32 72 b2 40 8a 66 11  |.X^s.Ou..2r.@.f.|
000000d0  9e 7b 04 c6 47 02 0e 72  35 75 0c 88 57 40 c4 4e  |.{..G..r5u..W@.N|
000000e0  08 89 4f 1c 8c 47 1e 79  06 8a 4e 12 88 4f 25 80  |..O..G.y..N..O%.|
000000f0  c7 02 81 7f fe 55 aa 75  85 81 7f fa cd 19 75 09  |.....U.u......u.|
00000100  c6 47 fa e9 c7 47 fb 94  88 e8 1c 00 ff e4 74 ce  |.G...G........t.|
00000110  88 57 24 eb c9 5d 33 c0  8e d8 8e c0 8e d0 bc 00  |.W$..]3.........|
00000120  7c 55 bd a2 07 fc fb c3  b4 08 52 06 cd 13 07 72  ||U........R....r|
00000130  33 33 db 8a de 8b 46 0a  33 d2 83 e1 3f f7 f1 91  |33....F.3...?...|
00000140  97 8b 46 08 f7 f7 42 87  ca 3b da 72 17 43 f7 f3  |..F...B..;.r.C..|
00000150  8a f2 86 c5 d1 e8 d1 e8  0a c8 d0 cc d0 cc 0a f4  |................|
00000160  84 e4 74 02 b4 41 5b 8a  d3 c3 0d 0a 4d 42 52 20  |..t..A[.....MBR |
00000170  45 72 72 6f 72 20 00 0d  0a 00 72 65 73 73 20 61  |Error ....ress a|
00000180  6e 79 20 6b 65 79 20 74  6f 20 62 6f 6f 74 20 66  |ny key to boot f|
00000190  72 6f 6d 20 66 6c 6f 70  70 79 2e 2e 2e 00 00 00  |rom floppy......|
000001a0  00 00 10 00 01 00 00 7c  00 00 af 2f 7f 10 00 00  |.......|.../....|
000001b0  00 00 80 00 00 05 0e 00  d8 fb f3 4f 00 00 80 01  |...........O....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 01 37 77 11 00 fe  |......?....7w...|
000001d0  ff ff 07 fe ff ff 40 37  77 11 41 0e a5 0b 00 00  |......@7w.A.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by keepitsimpleengr on 2009-05-04
This has resolved itself, so to speak, albeit very strange.

After running setup (hd3,0) from GRUB with root set to the 9.04 partition mounted on a directory from LiveCD session, now booting from /dev/sdb1 properly boots the 9.04 system.   Apparently the original install put GRUB on this disk, a prior OEL/RHEL installation instead of this 9.04/8.10… Ubuntu install disk.  Go Figure…

Now to get the upgrade to work.

Thanks John.

---

### Post by keepitsimpleengr on 2009-05-04
..

---

