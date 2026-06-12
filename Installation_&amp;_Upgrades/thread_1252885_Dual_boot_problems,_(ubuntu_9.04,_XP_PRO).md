---
title: "Dual boot problems, (ubuntu 9.04, XP PRO)"
date: 2009-08-29
forum: Installation &amp; Upgrades
---

### Post by ElevenWarrior on 2009-08-29
I've got Ubuntu 9.04  installed, I go to install XP Pro, and it says there is no disk. at all.
any ideas?
(the drive is 250 GB, 100GB ext4, 3 GB swap, 30 GB un-allocated, 100NTFS, (If formatted it in ubuntu)

---

### Post by argos3016 on 2009-08-29
The only way I think is that you must unistall Ubuntu and format at (low level?) all hard drive.
At  another ubunter, do you have any idea?

---

### Post by tal007 on 2009-08-29
Windows XP will not be able recognize your Hard Drive, because Ubuntu is very different ( e.g File System type etc..) from XP.
The only way you can install XP on it -  by removing the partition table. I am assuming that you are trying to install XP on your drive by removing Ubuntu. To do that, you must boot your system from a floppy using a generic boot disk ( generic windows 98 or Dos ). You also need a utility called delpart.exe to delete your partition table. Both has to run from the floppy. I must caution, it takes some time to boot the system ( 7 or 8 minutes ). Same goes for the delpart.exe. It takes some time to show up on your display from the time you have executed delpart.exe.

Files you need : 1. win_boot
                 2. delpart.exe

Search on the internet. They are still around. I just downloaded
win_boot several days ago. Keep in mind, when you transfer win_boot, you must do it the proper way. Otherwise the it won't work.  

Try this, it will work. If not, there another alternative.



Boot it from floppy.
Make sure it is generic win98 or Dos boot disk.

a:>

a:> delaprt.exe

It takes long, so don't assume the system has stalled.

---

### Post by charm_quark on 2009-08-29
well i think it the way you are trying to install ubuntu ! when i first tried to dual boot, my window system would tell me the my 250GB was actually a 500Gb [(my horrific experience)]("http://www.driverheaven.net/linux-operating-systems/183899-linux-boot.html#post1263602")
... hope that thread helps! :roll:

---

### Post by linux_tech on 2009-08-29
If you are installing to a sata disk then you may need to find and download the sata drivers for the disk.

A reference for you - How to dual boot Linux and Windows XP if Linux is installed first- 
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by tal007 on 2009-08-29
If you are trying to run dual boot then you may have to resize your drive if you have allocated your entire drive to Ubuntu. Leave space large enough for XP installation. 



Before

------------------------------------------------------
|                        Ubuntu



Resize your drive.
Leave a partition large enough for XP.
Delete the resized partition afterward
so that XP does not see it as Ubuntu partition.



-----------------------------------------------
Ubuntu             ||      Delete this newly
                           created partition
                           so that Windows Xp
                           does not see this area 
                           belonging to Ubuntu

---

### Post by ElevenWarrior on 2009-08-30
@ linux_tech, very right about sata drivers. I was wondering if I'd need them. I'm trying the tutorial now.
@ Tal007, I've already tried that, there's enough space, I don't want to have to re-install ubuntu though. 
Update, Windows woln't pick up my HD, there's already space there for it, unallocated, it just doesn't see it.

@charm_quark, your welcome, I've been using linux for 1 year and a half.
@argos3016 thanks for responding, I know there's another way though.

---

### Post by ElevenWarrior on 2009-09-04
alright, I've got XP PRO installed, and ubuntu
this is what my GRUB looks like,


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
timeout		3

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
# kopt=root=UUID=bf4673aa-af7d-4801-8156-319eb3aaba28 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=bf4673aa-af7d-4801-8156-319eb3aaba28

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

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		bf4673aa-af7d-4801-8156-319eb3aaba28
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=bf4673aa-af7d-4801-8156-319eb3aaba28 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		bf4673aa-af7d-4801-8156-319eb3aaba28
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=bf4673aa-af7d-4801-8156-319eb3aaba28 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		bf4673aa-af7d-4801-8156-319eb3aaba28
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=bf4673aa-af7d-4801-8156-319eb3aaba28 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		bf4673aa-af7d-4801-8156-319eb3aaba28
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=bf4673aa-af7d-4801-8156-319eb3aaba28 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		bf4673aa-af7d-4801-8156-319eb3aaba28
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows XP
root (hd0,1)
makeactive
chainloader +1 

problem is, I boot into XP, and is says device no ready... any ideas?

---

### Post by presence1960 on 2009-09-04
Let's get a better look at your setup. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

We need to see exactly what your setup is and your boot process. We can guess all day long or we can see for sure what you have by running the script.

---

### Post by ElevenWarrior on 2009-09-04
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2bab359d

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   195,318,269   195,318,207  83 Linux
/dev/sda2         195,318,270   279,306,089    83,987,820   5 Extended
/dev/sda5         195,318,333   201,181,994     5,863,662  82 Linux swap / Solaris
/dev/sda3    *    279,306,090   488,392,064   209,085,975   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="bf4673aa-af7d-4801-8156-319eb3aaba28" TYPE="ext4" 
/dev/sda3: UUID="BC1811C618118116" TYPE="ntfs" 
/dev/sda5: UUID="5dbc9446-e548-1c97-d306-b926750a6b2d" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ownera/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ownera)


=========================== sda1/boot/grub/menu.lst: ===========================

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
timeout		3

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
# kopt=root=UUID=bf4673aa-af7d-4801-8156-319eb3aaba28 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=bf4673aa-af7d-4801-8156-319eb3aaba28

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

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		bf4673aa-af7d-4801-8156-319eb3aaba28
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=bf4673aa-af7d-4801-8156-319eb3aaba28 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		bf4673aa-af7d-4801-8156-319eb3aaba28
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=bf4673aa-af7d-4801-8156-319eb3aaba28 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		bf4673aa-af7d-4801-8156-319eb3aaba28
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=bf4673aa-af7d-4801-8156-319eb3aaba28 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		bf4673aa-af7d-4801-8156-319eb3aaba28
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=bf4673aa-af7d-4801-8156-319eb3aaba28 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		bf4673aa-af7d-4801-8156-319eb3aaba28
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows XP
root (hd0,1)
makeactive
chainloader +1 

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=bf4673aa-af7d-4801-8156-319eb3aaba28 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5dbc9446-e548-1c97-d306-b926750a6b2d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   5.5GB: boot/grub/menu.lst
   1.7GB: boot/grub/stage2
   1.7GB: boot/initrd.img-2.6.28-11-generic
   8.9GB: boot/initrd.img-2.6.28-15-generic
   1.8GB: boot/vmlinuz-2.6.28-11-generic
    .6GB: boot/vmlinuz-2.6.28-15-generic
   8.9GB: initrd.img
   1.7GB: initrd.img.old
    .6GB: vmlinuz
   1.8GB: vmlinuz.old

================================ sda3/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer

=======Devices which don't seem to have a corresponding hard drive==============

sdb

---

### Post by presence1960 on 2009-09-04
boot into ubuntu and run this command from terminal ```
gksu gedit /boot/grub/menu.lst
``` that is a lowercase L in .lst

scroll to the bottom and change your windows entry to

```
### END DEBIAN AUTOMAGIC KERNELS LIST

title       Windows XP
root        (hd0,2)
makeactive
chainloader +1

```
click Save on the toolbar, close the file & reboot. Try the windows entry on GRUB. report back what happens.

P.S you can't boot windows because your windows entry has root (hd0,1) which is your extended partition.Numbering in GRUB for disks & partitions starts at 0. sda = (hd0), sdb = (hd1). sda1 = (hd0,0), sda2 = (hd0,1), etc. sdb1 = (hd1,0), sdb2 = (hd1,1), etc.

your windows is on sda3. sda3 = (hd0,2)

---

### Post by presence1960 on 2009-09-04
> **tal007 said:**
> If you are trying to run dual boot then you may have to resize your drive if you have allocated your entire drive to Ubuntu. Leave space large enough for XP installation. 



Before

------------------------------------------------------
|                        Ubuntu



Resize your drive.
Leave a partition large enough for XP.
Delete the resized partition afterward
so that XP does not see it as Ubuntu partition.



-----------------------------------------------
Ubuntu             ||      Delete this newly
                           created partition
                           so that Windows Xp
                           does not see this area 
                           belonging to Ubuntu

If you format the newly created partition as NTFS the XP installer will recognize it and install to it. If you leave it unformatted the same thing will happen, the XP installer will recognize it. 
If you are familiar with the windows installer you can format & install windows to any partition the installer recognizes regardless of what OS "it belongs to". That phrase "it belongs to" is BS. Partitions do not belong to anything. They are formatted as a filesystem (NTFS, FAT, ext3, ext4, etc) and may or may not have data or an OS within them. If they have data or an OS within them a format will clear that and then they may be used to install an OS onto. Of course one should back up any data they don't want to lose prior to formatting.

---

### Post by presence1960 on 2009-09-04
> **argos3016 said:**
> The only way I think is that you must unistall Ubuntu and format at (low level?) all hard drive.
At  another ubunter, do you have any idea?

absolutely false!

---

### Post by presence1960 on 2009-09-04
> **tal007 said:**
> Windows XP will not be able recognize your Hard Drive, because Ubuntu is very different ( e.g File System type etc..) from XP.
The only way you can install XP on it -  by removing the partition table. I am assuming that you are trying to install XP on your drive by removing Ubuntu. To do that, you must boot your system from a floppy using a generic boot disk ( generic windows 98 or Dos ). You also need a utility called delpart.exe to delete your partition table. Both has to run from the floppy. I must caution, it takes some time to boot the system ( 7 or 8 minutes ). Same goes for the delpart.exe. It takes some time to show up on your display from the time you have executed delpart.exe.

Files you need : 1. win_boot
                 2. delpart.exe

Search on the internet. They are still around. I just downloaded
win_boot several days ago. Keep in mind, when you transfer win_boot, you must do it the proper way. Otherwise the it won't work.  

Try this, it will work. If not, there another alternative.



Boot it from floppy.
Make sure it is generic win98 or Dos boot disk.

a:>

a:> delaprt.exe

It takes long, so don't assume the system has stalled.

What in the world are you talking about? Disregard this info. All you need to do is resize your ubuntu partition with gparted and create either unallocated space or an NTFS partition for windows to use. Then boot the windows installation CD and install windows to the NTFS partition or the unallocated space.

---

### Post by ElevenWarrior on 2009-09-04
> **presence1960 said:**
> boot into ubuntu and run this command from terminal ```
gksu gedit /boot/grub/menu.lst
``` that is a lowercase L in .lst

scroll to the bottom and change your windows entry to

```
### END DEBIAN AUTOMAGIC KERNELS LIST

title       Windows XP
root        (hd0,2)
makeactive
chainloader +1

```
click Save on the toolbar, close the file & reboot. Try the windows entry on GRUB. report back what happens.

P.S you can't boot windows because your windows entry has root (hd0,1) which is your extended partition.Numbering in GRUB for disks & partitions starts at 0. sda = (hd0), sdb = (hd1). sda1 = (hd0,0), sda2 = (hd0,1), etc. sdb1 = (hd1,0), sdb2 = (hd1,1), etc.

your windows is on sda3. sda3 = (hd0,2)

thank you this worked! marking as SLOVED

---

### Post by presence1960 on 2009-09-04
> **ElevenWarrior said:**
> thank you this worked! marking as SLOVED

Glad you got it working, enjoy Ubuntu!

P.S. simple problem = simple solution!

---

### Post by siyisoy on 2009-09-05
Hi
I have a similar problem. I installed Ubuntu 9.04 to an existing windows install. Windows was at the primary partition and I used free space when I was installing Ubuntu. Ubuntu works fine but Windows is not booting at all. Windows safe mode menu selection comes up and whatever I choose from that menu I get a blue screen.
Here is my bootscript result

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       26626256 sectors, but according to the info from 
                       fdisk, it has 26635707 sectors.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0007569c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    26,635,769    26,635,707   7 HPFS/NTFS
/dev/sda2          26,635,770    58,605,119    31,969,350   f W95 Ext d (LBA)
/dev/sda5          26,635,833    57,625,154    30,989,322  83 Linux
/dev/sda6          57,625,218    58,605,119       979,902  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="602C3A112C39E2A8" TYPE="ntfs" 
/dev/sda5: UUID="e46c59d8-a21a-4fb7-9079-769084bdc10a" TYPE="ext4" 
/dev/sda6: TYPE="swap" UUID="2ce9c155-b067-4123-ae0f-c831d30cf258" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext4 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/wyginwys/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=wyginwys)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=e46c59d8-a21a-4fb7-9079-769084bdc10a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e46c59d8-a21a-4fb7-9079-769084bdc10a

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

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		e46c59d8-a21a-4fb7-9079-769084bdc10a
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=e46c59d8-a21a-4fb7-9079-769084bdc10a ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		e46c59d8-a21a-4fb7-9079-769084bdc10a
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=e46c59d8-a21a-4fb7-9079-769084bdc10a ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		e46c59d8-a21a-4fb7-9079-769084bdc10a
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=e46c59d8-a21a-4fb7-9079-769084bdc10a ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		e46c59d8-a21a-4fb7-9079-769084bdc10a
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=e46c59d8-a21a-4fb7-9079-769084bdc10a ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		e46c59d8-a21a-4fb7-9079-769084bdc10a
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=e46c59d8-a21a-4fb7-9079-769084bdc10a /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2ce9c155-b067-4123-ae0f-c831d30cf258 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  15.3GB: boot/grub/menu.lst
  15.4GB: boot/grub/stage2
  15.6GB: boot/initrd.img-2.6.28-11-generic
  16.3GB: boot/initrd.img-2.6.28-15-generic
  15.5GB: boot/vmlinuz-2.6.28-11-generic
  14.2GB: boot/vmlinuz-2.6.28-15-generic
  16.3GB: initrd.img
  15.6GB: initrd.img.old
  14.2GB: vmlinuz
  15.5GB: vmlinuz.old

---

### Post by presence1960 on 2009-09-05
```
============================= Boot Info Summary: ==============================

=> Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive
in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: According to the info in the boot sector, sda1 has
26626256 sectors, but according to the info from
fdisk, it has 26635707 sectors.
Operating System: Windows XP
Boot files/dirs: /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________ _______________________

File system: Extended Partition
Boot sector type: -
Boot sector info:

sda5: __________________________________________________ _______________________

File system: ext4
Boot sector type: -
Boot sector info:
Operating System: Ubuntu 9.04
Boot files/dirs: /boot/grub/menu.lst /etc/fstab

sda6: __________________________________________________ _______________________

File system: swap
Boot sector type: -
Boot sector info:

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ __________________________________________________ ___

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0007569c

Partition Boot Start End Size Id System

/dev/sda1 * 63 26,635,769 26,635,707 7 HPFS/NTFS
/dev/sda2 26,635,770 58,605,119 31,969,350 f W95 Ext d (LBA)
/dev/sda5 26,635,833 57,625,154 30,989,322 83 Linux
/dev/sda6 57,625,218 58,605,119 979,902 82 Linux swap / Solaris


blkid -c /dev/null: __________________________________________________ __________

/dev/sda1: UUID="602C3A112C39E2A8" TYPE="ntfs"
/dev/sda5: UUID="e46c59d8-a21a-4fb7-9079-769084bdc10a" TYPE="ext4"
/dev/sda6: TYPE="swap" UUID="2ce9c155-b067-4123-ae0f-c831d30cf258"

=============================== "mount" output: ===============================

/dev/sda5 on / type ext4 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/wyginwys/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=wyginwys)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOW S

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Micro soft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=e46c59d8-a21a-4fb7-9079-769084bdc10a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e46c59d8-a21a-4fb7-9079-769084bdc10a

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
## indomU=true
## indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 9.04, kernel 2.6.28-15-generic
uuid e46c59d8-a21a-4fb7-9079-769084bdc10a
kernel /boot/vmlinuz-2.6.28-15-generic root=UUID=e46c59d8-a21a-4fb7-9079-769084bdc10a ro quiet splash
initrd /boot/initrd.img-2.6.28-15-generic
quiet

title Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid e46c59d8-a21a-4fb7-9079-769084bdc10a
kernel /boot/vmlinuz-2.6.28-15-generic root=UUID=e46c59d8-a21a-4fb7-9079-769084bdc10a ro single
initrd /boot/initrd.img-2.6.28-15-generic

title Ubuntu 9.04, kernel 2.6.28-11-generic
uuid e46c59d8-a21a-4fb7-9079-769084bdc10a
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=e46c59d8-a21a-4fb7-9079-769084bdc10a ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic
quiet

title Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid e46c59d8-a21a-4fb7-9079-769084bdc10a
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=e46c59d8-a21a-4fb7-9079-769084bdc10a ro single
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu 9.04, memtest86+
uuid e46c59d8-a21a-4fb7-9079-769084bdc10a
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# / was on /dev/sda5 during installation
UUID=e46c59d8-a21a-4fb7-9079-769084bdc10a / ext4 relatime,errors=remount-ro 0 1
# swap was on /dev/sda6 during installation
UUID=2ce9c155-b067-4123-ae0f-c831d30cf258 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

=================== sda5: Location of files loaded by Grub: ===================


15.3GB: boot/grub/menu.lst
15.4GB: boot/grub/stage2
15.6GB: boot/initrd.img-2.6.28-11-generic
16.3GB: boot/initrd.img-2.6.28-15-generic
15.5GB: boot/vmlinuz-2.6.28-11-generic
14.2GB: boot/vmlinuz-2.6.28-15-generic
16.3GB: initrd.img
15.6GB: initrd.img.old
14.2GB: vmlinuz
15.5GB: vmlinuz.old
```
First thing next time you post a lot of text highlight all the text and click the # sign on the toolbar to place code tags around the text. See how it works, I copied your boot info script from your post and did that. Thanks for your cooperation!

Your boot info script looks OK. Did you defrag windows at least once or twice prior to shrinking it? The blue screen of death is a windows problem. I would use the windows install disk and see if you can run chkdsk from the command prompt. Boot off the windows install CD. Choose repair. When the command prompt appears run ```
chkdsk c: /f
```
if that does not fix it you may have to reinstall windows. if you do that you will have to restore GRUB to MBR after the windows installation as windows will write it's bootloader over GRUB. That is a simple 45 second fix. Do this after windows is installed:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,4)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,4)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

In #6 use setup (hd0) to put GRUB on the MBR.

You should now be good to go.
```

P.s. you should be able to copy any files from your windows partition that you don't want to lose from within Ubuntu.

---

### Post by siyisoy on 2009-09-05
I forgot to mention that I tried XP install cd and it doesnt recognise the hard drive.
I tried chkdsk c: /f but it gives me errors like no disk.

I need to add that fdisk gives such a warning

```
The number of cylinders for this disk is set to 3648.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

```

Also I didnt shrink windows partition before I install Ubuntu.

---

### Post by presence1960 on 2009-09-05
> **siyisoy said:**
> I forgot to mention that I tried XP install cd and it doesnt recognise the hard drive.
I tried chkdsk c: /f but it gives me errors like no disk.

I need to add that fdisk gives such a warning

```
The number of cylinders for this disk is set to 3648.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

```

Also I didnt shrink windows partition before I install Ubuntu.
Well you may have to reinstall windows. just follow the instructions from my last post to reinstall GRUB to the MBR after windows is installed.

if you don't want to reinstall windows then you might want to go to microsoft's site to troubleshoot your BSOD error codes.

---

### Post by siyisoy on 2009-09-05
I want to install Windows but install cd doesnt recognise the hard drive. So I am stucked.
I think the problem is related with MBR.

---

### Post by presence1960 on 2009-09-05
> **siyisoy said:**
> I want to install Windows but install cd doesnt recognise the hard drive. So I am stucked.
I think the problem is related with MBR.

Boot from the ubuntu Live Cd and choose "try ubuntu without any changes", when the desktop loads use gparted to delete the sda1 Windows partition. You can access gparted by either opening a terminal and running the command ```
gksu gparted
```
OR going System > Administration > Partition Editor. When gparted loads right click on the windows partition sda1 and choose delete. Then click Apply (green check mark) at the top toolbar.

After that is applied you can leave it as unallocated space. Windows installer should recognize that or you can create a partition from the unallocated space as an NTFS primary partition. Windows must be on a primary partition.

---

### Post by siyisoy on 2009-09-05
> **presence1960 said:**
> 
After that is applied you can leave it as unallocated space. Windows installer should recognize that or you can create a partition from the unallocated space as an NTFS primary partition. Windows must be on a primary partition.
I dont think it will recognise the unallocated space because it doesnt recognise the whole drive. How come will it recognise some part of it?

---

### Post by presence1960 on 2009-09-05
> **siyisoy said:**
> I dont think it will recognise the unallocated space because it doesnt recognise the whole drive. How come will it recognise some part of it?
If you don't want to try it then don't do it. What have you got to lose.

Or you can scrub both installs format the entire hard disk and reinstall Windows then Ubuntu.

---

### Post by siyisoy on 2009-09-06
I deleted the primary NTFS partition and tried to install windows. But as I guessed the installer didnt recognise the hard drive so I couldnt install it. Now I am thinking what would happen if I format the hard drive with Ubuntu.

---

### Post by Bartender on 2009-09-06
Is this a SATA or PATA HDD?  Are your connections tight?  I had a weird deal with a PATA dual-boot HDD a while back.  Windows would boot but Ubuntu wouldn't.  I'd been futzing with the cables inside and had knocked the PATA ribbon cable loose.

---

### Post by ElevenWarrior on 2009-09-06
what you should do is find out the make of the drive, and get the driver for it and slipstream it with Nlite. thats what I had to do with my problem.

---

### Post by siyisoy on 2009-09-07
I reformatted the hard drive with Ubuntu Live CD. Tried to install windows without success. Ubuntu installs correctly but windows dont see the hard drive. 
I know something strange had happened to my laptop. I think it is related with MBR. It is an old laptop IBM Thinkpad R40e.There was an IBM program about booting,configs etc which is preloaded. I made some different OS installs. And that program is gone. Now It has only its basic BIOS program. 
Lastly  I installed Windows XP and after that Ubuntu with dual boot. After installing Ubuntu Windows didnt open. I formatted everything. And now windows cd dont see the hard drive.

---

### Post by ElevenWarrior on 2009-09-13
did you even read me post?

---

