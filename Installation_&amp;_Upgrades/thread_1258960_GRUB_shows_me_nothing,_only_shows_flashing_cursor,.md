---
title: "GRUB shows me nothing, only shows flashing cursor, can't boot anything"
date: 2009-09-05
forum: Installation &amp; Upgrades
---

### Post by grenadier32 on 2009-09-05
So my Ubuntu and my Windows Vista are completely screwed up.

First I resized Vista's partition to give it a bit more space. This screwed it up--it couldn't boot Vista anymore. FIne, I understand why that screwed it up--not an issue to solve here, I can chkdsk it on another machine if I have to.

But, then I used testdisk to try to fix it (it said it repaired the MBR and MFT, but didn't), and ran grub from the command line to fix it--I did find /boot/grub/stage1 and root (hd0,3), but didn't run the setup (hd0) part.

Now when I boot, I get nothing but a flashing cursor. Oddly, I can only get to a live CD when I physically remove the hard drive. However, from a live CD I can view and copy the files on both partitions once it's booted.

Here's bootscript output...

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #4 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
ntfs_mst_post_read_fixup: Invalid argument
Actual VCN (0x3003800010001) of index buffer is different from expected VCN (0x0).
Failed to mount '/dev/sda2': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
ntfs_mst_post_read_fixup: Invalid argument
Actual VCN (0x3003800010001) of index buffer is different from expected VCN (0x0).
Failed to mount '/dev/sda2': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x90000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       192,779       192,717  de Dell Utility
/dev/sda2             192,780    12,434,309    12,241,530   7 HPFS/NTFS
/dev/sda3    *     12,434,310   121,178,294   108,743,985   7 HPFS/NTFS
/dev/sda4         121,178,295   625,137,344   503,959,050  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D8-0B06" TYPE="vfat" 
/dev/sda2: UUID="A676F6D776F6A769" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda3: UUID="30C4F9B9C4F98200" LABEL="OS" TYPE="ntfs" 
/dev/sda4: UUID="6329b15b-19b2-4273-96d6-d7b13ebb4c69" SEC_TYPE="ext2" TYPE="ext3" 

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


=========================== sda4/boot/grub/menu.lst: ===========================

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=6329b15b-19b2-4273-96d6-d7b13ebb4c69 ro i8042.nomux=1

## default grub root device
## e.g. groot=(hd0,0)
# groot=6329b15b-19b2-4273-96d6-d7b13ebb4c69

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
# defoptions=splash

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

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		6329b15b-19b2-4273-96d6-d7b13ebb4c69
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=6329b15b-19b2-4273-96d6-d7b13ebb4c69 ro i8042.nomux=1 splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		6329b15b-19b2-4273-96d6-d7b13ebb4c69
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=6329b15b-19b2-4273-96d6-d7b13ebb4c69 ro i8042.nomux=1  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		6329b15b-19b2-4273-96d6-d7b13ebb4c69
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=6329b15b-19b2-4273-96d6-d7b13ebb4c69 ro i8042.nomux=1 splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		6329b15b-19b2-4273-96d6-d7b13ebb4c69
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=6329b15b-19b2-4273-96d6-d7b13ebb4c69 ro i8042.nomux=1  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		6329b15b-19b2-4273-96d6-d7b13ebb4c69
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=6329b15b-19b2-4273-96d6-d7b13ebb4c69 ro i8042.nomux=1 splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		6329b15b-19b2-4273-96d6-d7b13ebb4c69
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=6329b15b-19b2-4273-96d6-d7b13ebb4c69 ro i8042.nomux=1  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, memtest86+
uuid		6329b15b-19b2-4273-96d6-d7b13ebb4c69
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1


=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4: Ubuntu root
UUID=6329b15b-19b2-4273-96d6-d7b13ebb4c69 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2: Dell's recovery thing
UUID=A676F6D776F6A769 /media/recovery ntfs    defaults,umask=007,uid=1000,gid=46 0       1
# /dev/sda3: Vista's lame 50 GB
UUID=30C4F9B9C4F98200 /media/windows  ntfs    defaults,umask=007,uid=1000,gid=46 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# SSHFS: skeith:/home/mickey
#sshfs#mickey@skeith.homelinux.net:/home/mickey /home/mickey/Skeith fuse user,noauto,allow_other 0 0
#Swap on /media/recovery... may be unsafe?
/media/recovery/swapfile   swap  swap  defaults 0  0

=================== sda4: Location of files loaded by Grub: ===================


 269.3GB: boot/grub/menu.lst
 269.3GB: boot/grub/stage2
 269.3GB: boot/initrd.img-2.6.28-13-generic
 269.4GB: boot/initrd.img-2.6.28-14-generic
 270.5GB: boot/initrd.img-2.6.28-15-generic
 269.3GB: boot/vmlinuz-2.6.28-13-generic
 269.3GB: boot/vmlinuz-2.6.28-14-generic
 270.6GB: boot/vmlinuz-2.6.28-15-generic
 270.5GB: initrd.img
 269.4GB: initrd.img.old
 270.6GB: vmlinuz
 269.3GB: vmlinuz.old
```

fdisk -l gives me this...

```
ubuntu@ubuntu:~/Desktop$ sudo fdisk -l /dev/sda

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          12       96358+  de  Dell Utility
/dev/sda2              13         774     6120765    7  HPFS/NTFS
/dev/sda3   *         775        7543    54371992+   7  HPFS/NTFS
/dev/sda4            7544       38913   251979525   83  Linux
```

update-grub and grub-install --recheck --root-directory=/media/disk (with the drive mounted) don't help either, even though they say they work.

Any insights? Is there a way to completely remove GRUB and reinstall it?

---

### Post by stlsaint on 2009-09-05
i noticed that sda3 has no boot files or dir's showing so i think that may be why you are not able to boot vista. also you do need to install Grub (hd0) go thru the same steps you stated before..../boot/grub/stage1 etc etc but run the setup cmd and  install grub there...then youll be able to boot into linux and can re-add the vista stanza again to menu.lst.

---

### Post by grenadier32 on 2009-09-05
> **stlsaint said:**
> i noticed that sda3 has no boot files or dir's showing so i think that may be why you are not able to boot vista. also you do need to install Grub (hd0) go thru the same steps you stated before..../boot/grub/stage1 etc etc but run the setup cmd and  install grub there...then youll be able to boot into linux and can re-add the vista stanza again to menu.lst.

Wait, what do you mean? You mean install GRUB with (hd0,2), the same as /dev/sda3, as root?

---

### Post by stlsaint on 2009-09-05
you only have 1 hdd installed right...so you want to setup grub to (hd0,0) the first hdd in boot and on the first partition...that will put Grub there so that you will be able to see Grub at boot. and i was saying about sda3 that thats where vista is but there are no boot/dir showing up in your bootscript so you need to recovery the vista partition to show that the boot files are there.

---

### Post by grenadier32 on 2009-09-05
Also note... I appear to have some errors on the NTFS partitions (/dev/sda2 and /dev/sda3), specifically, unaccounted for clusters. Would this complicate matters? I can't easily get into Windows to run chkdsk and fix it...

---

### Post by stlsaint on 2009-09-05
> **grenadier32 said:**
> Also note... I appear to have some errors on the NTFS partitions (/dev/sda2 and /dev/sda3), specifically, unaccounted for clusters. Would this complicate matters? I can't easily get into Windows to run chkdsk and fix it...

you can use either DaRT for Vista(google and download for free) or another recovery disk to run diagnostics on vista.

---

### Post by grenadier32 on 2009-09-05
> **stlsaint said:**
> you only have 1 hdd installed right...so you want to setup grub to (hd0,0) the first hdd in boot and on the first partition...that will put Grub there so that you will be able to see Grub at boot. and i was saying about sda3 that thats where vista is but there are no boot/dir showing up in your bootscript so you need to recovery the vista partition to show that the boot files are there.

So to confirm, I run sudo grub, then find /boot/grub/stage1 (which returns (hd0,3), then I do root (hd0,0) and then setup (hd0)? Or I set root to (hd0,3) and setup (hd0,0)?

---

### Post by stlsaint on 2009-09-05
yes if stage1 returns hd0,3 than that will be root and setup on hd0...make sure to fix sda3 too.

---

### Post by grenadier32 on 2009-09-05
```
       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd0,3)

grub> root (hd0,3)

grub> setup (hd0,0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,3)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,0) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.
```

---

### Post by stlsaint on 2009-09-05
if you cant see grub or boot into ubuntu than do same as before but use hd0,3 as setup instead of hd0,0
also see links in my sig for better explanations. i dont want to do anything to mess with your system if im confusing or anything.

---

### Post by grenadier32 on 2009-09-05
> **stlsaint said:**
> if you cant see grub or boot into ubuntu than do same as before but use hd0,3 as setup instead of hd0,0
also see links in my sig for better explanations. i dont want to do anything to mess with your system if im confusing or anything.

The setup (hd0,0) didn't work--I'll try (hd0,3):

```
       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1 
 (hd0,3)

grub> root (hd0,3)

grub> setup (hd0,3)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,3)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,3)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,3) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.
```

I don't suppose this embed failure matters at all? If it can't embed ext2 handling, wouldn't that explain its failure to boot? At any rate, I'm trying now.

---

### Post by grenadier32 on 2009-09-05
It didn't work. :( Any other suggestions? Could that broken stage1.5 embed be a problem?

---

### Post by stlsaint on 2009-09-05
you may want to consider re-installing ubuntu

---

### Post by presence1960 on 2009-09-05
> **stlsaint said:**
> i noticed that sda3 has no boot files or dir's showing so i think that may be why you are not able to boot vista. also you do need to install Grub (hd0) go thru the same steps you stated before..../boot/grub/stage1 etc etc but run the setup cmd and  install grub there...then youll be able to boot into linux and can re-add the vista stanza again to menu.lst.

sda2 is probably his Vista OS partition, not only does it have boot files/dir but it is all messed up (see errors). Did you resize vista with gparted. if so big mistake there is a documented unresolved bug when resizing Vista with anything other than Vista's disk management utility. See [here]("http://bugzilla.gnome.org/show_bug.cgi?id=379482").

This is what I would do. back up any Ubuntu files you don't want to lose. If you have a Vista install DVD boot from it and do [this]("http://ubuntuforums.org/showthread.php?t=1014708").
If all you have is a recovery partition/DVD then download the Vista recovery console iso from [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") and burn it as an image to CD. boot from the CD and do the same procedure I listed above. This should get Vista booting again. You will boot straight into Vista when you boot because that procedure will rewrite Vista to MBR. Then install Ubuntu and GRUB will be back on MBR.

---

### Post by grenadier32 on 2009-09-05
> **presence1960 said:**
> This is what I would do. back up any Ubuntu files you don't want to lose. If you have a Vista install DVD boot from it and do [this]("http://ubuntuforums.org/showthread.php?t=1014708").
If all you have is a recovery partition/DVD then download the Vista recovery console iso from [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") and burn it as an image to CD. boot from the CD and do the same procedure I listed above. This should get Vista booting again. You will boot straight into Vista when you boot because that procedure will rewrite Vista to MBR. Then install Ubuntu and GRUB will be back on MBR.

The problem is, I've repeatedly tried getting GRUB working again with that method from a live CD--it just keeps giving me the flashing cursor and nothing else. The other problem is, for some reason, when I have the hard drive plugged in, live CDs refuse to boot! I have to physically remove the hard drive in order to get a live CD to do anything! I find that part the most bizarre, and I think it points to something other than GRUB being the culprit. And even more weirdly, if I plug the drive back in after the live CD comes up, I'm able to view the files on the drive just fine.

Unfortunately, I can't restore Vista's bootloader from a Vista CD because of that same problem--the machine won't boot to Vista's installation disc if the hard drive is plugged in, and the disc won't acknowledge the drive after it's come up.

Does this give you any insight? :(

---

### Post by presence1960 on 2009-09-06
> **grenadier32 said:**
> The problem is, I've repeatedly tried getting GRUB working again with that method from a live CD--it just keeps giving me the flashing cursor and nothing else. The other problem is, for some reason, when I have the hard drive plugged in, live CDs refuse to boot! I have to physically remove the hard drive in order to get a live CD to do anything! I find that part the most bizarre, and I think it points to something other than GRUB being the culprit. And even more weirdly, if I plug the drive back in after the live CD comes up, I'm able to view the files on the drive just fine.

Unfortunately, I can't restore Vista's bootloader from a Vista CD because of that same problem--the machine won't boot to Vista's installation disc if the hard drive is plugged in, and the disc won't acknowledge the drive after it's come up.

Does this give you any insight? :(
That is because your stage 1.5 is messed up. if you reinstall Ubuntu after fixing windows you will have a fresh install with all parts of GRUB installed. if you install Ubuntu with windows already installed you won't have to use the Live Cd to restore GRUB.

if you can't boot from a bootable CD then you have a hardware problem. Try installing Ubuntu from a bootable USB if your machine will boot from USB. You can use [unetbootin]("http://unetbootin.sourceforge.net/") to create a bootable USB from the Live CD iso.

Do you have a IDE hard disk & IDE optical drive. maybe your cable is connected to both of them incorrectly (slave/master) or you have jumpers set incorrectly. Whatever the problem is it is most likely hardware related.

---

### Post by grenadier32 on 2009-09-06
> **presence1960 said:**
> That is because your stage 1.5 is messed up. if you reinstall Ubuntu after fixing windows you will have a fresh install with all parts of GRUB installed. if you install Ubuntu with windows already installed you won't have to use the Live Cd to restore GRUB.

Is there any way to repair it? It seems like that should be the quickest way to fix it without reinstalling, assuming that's the problem that's reducing GRUB to nothing but a flashing cursor without so much as an error message. :-/

> **presence1960 said:**
> if you can't boot from a bootable CD then you have a hardware problem. Try installing Ubuntu from a bootable USB if your machine will boot from USB. You can use [unetbootin]("http://unetbootin.sourceforge.net/") to create a bootable USB from the Live CD iso.

Do you have a IDE hard disk & IDE optical drive. maybe your cable is connected to both of them incorrectly (slave/master) or you have jumpers set incorrectly. Whatever the problem is it is most likely hardware related.

It's SCSI, in a newer laptop--I can pretty easily take it in and out, and it boots to a live CD as long as the drive isn't plugged in. I can plug it back in once the live CD comes up to transfer files off and change things if necessary though.

---

### Post by presence1960 on 2009-09-06
> **grenadier32 said:**
> Is there any way to repair it? It seems like that should be the quickest way to fix it without reinstalling, assuming that's the problem that's reducing GRUB to nothing but a flashing cursor without so much as an error message. :-/



It's SCSI, in a newer laptop--I can pretty easily take it in and out, and it boots to a live CD as long as the drive isn't plugged in. I can plug it back in once the live CD comes up to transfer files off and change things if necessary though.

You can try from the Live Cd - boot to desktop and in terminal you can try ```
sudo grub-install /dev/sda
```

Sorry if I missed that. I assumed you tried that already.

---

### Post by grenadier32 on 2009-09-06
Sadly, I have tried that and it hasn't helped. :(

---

### Post by presence1960 on 2009-09-06
> **grenadier32 said:**
> Sadly, I have tried that and it hasn't helped. :(

looks like you may have to reinstall.

---

### Post by grenadier32 on 2009-09-06
I fixed it! Here's how I did it:

[LIST=1]
[*]Booted to an Ubuntu live CD.
[*]Cleared /dev/sda2 (Dell's recovery partition thing that I didn't need).
[*]Installed Ubuntu to that space. The installer figured out a new GRUB installation, and even figured out all the kernels on my existing one!
[*]Booted the existing installation (/dev/sda4), which came up fine!
[*]Ran update-grub and grub-install.
[/LIST]

Now it's working fine!

---

