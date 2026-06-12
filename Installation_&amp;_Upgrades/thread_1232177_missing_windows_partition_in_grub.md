---
title: "missing windows partition in grub"
date: 2009-08-05
forum: Installation &amp; Upgrades
---

### Post by codingfreak on 2009-08-05
HI 

I am facing a serious problem after installing UBUNTU 9.04 in my windows XP machine. When I restart the machine my GRUB menu dont have the XP option.

I am attaching the details of running the script "boot_info_script032.sh"

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive
    in partition #10 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts
                       at sector 63.
    Operating System:
    Boot files/dirs:

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts
                       at sector 63.
    Operating System:
    Boot files/dirs:

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts
                       at sector 63.
    Operating System:
    Boot files/dirs:

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda8 starts
                       at sector 63.
    Operating System:
    Boot files/dirs:

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda9 starts
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:

sda10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================
Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x92ea92ea

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     3,903,794     3,903,732  82 Linux swap / Solaris
/dev/sda2           3,903,795   312,560,639   308,656,845   f W95 Ext d (LBA)
/dev/sda5          30,716,343    71,682,029    40,965,687   7 HPFS/NTFS
/dev/sda6          71,682,093   112,647,779    40,965,687   7 HPFS/NTFS
/dev/sda7         112,647,843   174,080,339    61,432,497   7 HPFS/NTFS
/dev/sda8         174,080,403   235,512,899    61,432,497   7 HPFS/NTFS
/dev/sda9         235,512,963   312,560,639    77,047,677   7 HPFS/NTFS
/dev/sda10          3,903,921    30,716,279    26,812,359  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="f5195511-e1c6-41d0-99b2-24cd47739a30" TYPE="swap"
/dev/sda5: UUID="66A061B9A0618FFB" LABEL="SOFTWARES" TYPE="ntfs"
/dev/sda6: UUID="0EC8112EC8111615" LABEL="VIJAY(DON'T TUCH)" TYPE="ntfs"
/dev/sda7: UUID="9874352E7435108C" LABEL="MOVIES" TYPE="ntfs"
/dev/sda8: UUID="E4FC18B8FC188748" LABEL="SONGS" TYPE="ntfs"
/dev/sda9: UUID="90C8FDD7C8FDBB92" TYPE="ntfs"
/dev/sda10: UUID="7a848f48-de03-4fb8-a80b-284115ec6612" TYPE="ext3"

=============================== "mount" output: ===============================

/dev/sda10 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/harish/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=harish)
/dev/sda9 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda6 on /media/VIJAY(DON'T TUCH) type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda7 on /media/MOVIES type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /media/SOFTWARES type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda8 on /media/SONGS type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


========================== sda10/boot/grub/menu.lst: ==========================

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=7a848f48-de03-4fb8-a80b-284115ec6612 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7a848f48-de03-4fb8-a80b-284115ec6612

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
# defoptions=quiet splash

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
# howmany=all

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
title           Ubuntu 9.04, kernel 2.6.28-11-generic
uuid            7a848f48-de03-4fb8-a80b-284115ec6612
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=7a848f48-de03-4fb8-a80b-284115ec6612 ro quiet splash
initrd          /boot/initrd.img-2.6.28-11-generic
quiet

title           Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid            7a848f48-de03-4fb8-a80b-284115ec6612
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=7a848f48-de03-4fb8-a80b-284115ec6612 ro  single
initrd          /boot/initrd.img-2.6.28-11-generic

title           Ubuntu 9.04, memtest86+
uuid            7a848f48-de03-4fb8-a80b-284115ec6612
kernel          /boot/memtest86+.bin
quiet

title xp
root (hd0,1)
makeactive
chainloader +1
### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda10/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda10 during installation
UUID=7a848f48-de03-4fb8-a80b-284115ec6612 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
UUID=f5195511-e1c6-41d0-99b2-24cd47739a30 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda10: Location of files loaded by Grub: ===================


   2.3GB: boot/grub/menu.lst
   2.3GB: boot/grub/stage2
   2.4GB: boot/initrd.img-2.6.28-11-generic
   2.3GB: boot/vmlinuz-2.6.28-11-generic
   2.4GB: initrd.img
   2.3GB: vmlinuz

```So please guide me now how to solve the problem so that I can dual boot both windows xp and UBUNTU 9.04

---

### Post by louieb on 2009-08-05
Exactly what did you do to get the disk in this state. 1st thing I noticed all your NTFS partitions are logical partitions. Windows wants its boot loader in a primary partition. 

That leads to the 2nd thing  the script did not list any Windows boot loader files such as boot.ini or ntldr.  Does not look like you have a boot-able Windows partition.  

3rd thing is the only primary partition (sda1) is a Linux swap partition  and  it has the boot flag set.  Swap is similar to virtual memory in windows. It can't hold an OS to boot. This combination makes no sense.  

You will not be able to boot windows with GRUB until two things get done 1st. Windows need to be on a primary partition. And windows has to have its own boot loader GRUB does not boot windows - it passes control to windows boot loader (via the chainload command) and quits.

---

### Post by presence1960 on 2009-08-05
Codingfreak, louieb's assessment seems to be dead on. Your boot info script shows none of those windows partitions with boot files. Windows really needs to be on a primary partition. Some people have gotten GRUB to load windows from a logical partition, but with your partition table I don't think that may work: [https://www.linuxquestions.org/questions/linux-software-2/grub-windows-on-logical-partition-607114/](https://www.linuxquestions.org/questions/linux-software-2/grub-windows-on-logical-partition-607114/)

---

### Post by codingfreak on 2009-08-05
It seems I missed up really very badly ......

Can anyone give me a BEST and OPTIMIZED solution so that I can have both WINDOWS XP and UBUNTU .........

---

### Post by presence1960 on 2009-08-05
That will be a lot of work trying to redo all those partitions. I would use gparted either from the Ubuntu live Cd or gparted live CD to create new partitions beforehand and reinstall Windows & Ubuntu. of course back up your data first. If you do it this way you will install windows directly to a partition which means you won't have to shrink the windows partition to make room for ubuntu. You will already have all your partitions made. Remember that windows must be installed to a primary partition.

---

### Post by smudge12b on 2009-08-05
It is possible to reinstall windows after Ubuntu. If your Ubuntu is still working try this. 

[http://davestechsupport.com/blog/2008/03/22/how-to-install-windows-after-ubuntu-with-gparted/](http://davestechsupport.com/blog/2008/03/22/how-to-install-windows-after-ubuntu-with-gparted/)

I did it recently and it worked like a charm, at least you'll only have to reinstall rather than both OS

---

### Post by gordintoronto on 2009-08-05
Here's how I have my drive organized:
 - Windows 7 RC partition (60 GB)
 - Ubuntu / partition (40 GB)
 - swap partition (8 GB)
 - Ubuntu home partition (the rest)

My root partition is probably way too large, but if it got full it would be a disaster, and I can afford to give it the space.

All the best,
Gord


> **codingfreak said:**
> It seems I missed up really very badly ......

Can anyone give me a BEST and OPTIMIZED solution so that I can have both WINDOWS XP and UBUNTU .........

---

### Post by codingfreak on 2009-08-05
> **smudge12b said:**
> It is possible to reinstall windows after Ubuntu. If your Ubuntu is still working try this. 
 
[http://davestechsupport.com/blog/2008/03/22/how-to-install-windows-after-ubuntu-with-gparted/](http://davestechsupport.com/blog/2008/03/22/how-to-install-windows-after-ubuntu-with-gparted/)
 
I did it recently and it worked like a charm, at least you'll only have to reinstall rather than both OS
 
```
Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     3,903,794     3,903,732  82 Linux swap / Solaris
/dev/sda2           3,903,795   312,560,639   308,656,845   f W95 Ext d (LBA)
/dev/sda5          30,716,343    71,682,029    40,965,687   7 HPFS/NTFS
/dev/sda6          71,682,093   112,647,779    40,965,687   7 HPFS/NTFS
/dev/sda7         112,647,843   174,080,339    61,432,497   7 HPFS/NTFS
/dev/sda8         174,080,403   235,512,899    61,432,497   7 HPFS/NTFS
/dev/sda9         235,512,963   312,560,639    77,047,677   7 HPFS/NTFS
/dev/sda10          3,903,921    30,716,279    26,812,359  83 Linux
```
 
I am sure that my windows installation is in "/dev/sda9" So can I add something like below to my grub menu 
 
```
# This entry was added by username for a non-linux OS
# on /dev/sda9
title        Microsoft Windows XP Home Edition
root        [COLOR=#ff0000](hd0,7)[/COLOR]
savedefault
makeactive
chainloader    +1
```
 
Will it works ??

---

### Post by louieb on 2009-08-05
Did you try? Can't hurt. BTW sda9 in  GRUB would be (hd0,8).  the 1st logical partitions in GRUB is (hd0,4) does not matter how many primary partitions you have.
Thats ```
(hd0,8)
```
Probably will not work. Still need the windows boot loader to chainload to. 

Heres a little better explanation of how you might do it.[U][http://ubuntuforums.org/showpost.php?p=7488261&postcount=1]("http://ubuntuforums.org/showpost.php?p=7488261&postcount=17")[7]("http://ubuntuforums.org/showpost.php?p=7488261&postcount=17")

[/U]Might want to look at the whole thread [http://ubuntuforums.org/showthread.php?p=7488261#post7488261 ]("http://ubuntuforums.org/showthread.php?p=7488261#post7488261")
look at posts 17, 22, and 24

---

### Post by codingfreak on 2009-08-06
Installing WINDOWS XP in a logical partition really messed up my installation of UBUNTU.

It seems I should reinstall windows xp in a primary partition and then get the UBUNTU installed for proper dual boot machine ....

---

