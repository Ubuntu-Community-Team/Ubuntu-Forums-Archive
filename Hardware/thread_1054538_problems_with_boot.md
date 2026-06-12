---
title: "problems with boot"
date: 2009-01-29
forum: Hardware
---

### Post by mckinnley on 2009-01-29
i'm going to tell you all a very sad story involving a desktop and a grub. one day the happy little desktop computer was born, it was a special child, one that had top of the line parts, the best of their kind. unfortunately for this poor child it was installed with herpes(vista), so one day, the owner of this desktop came along and said to the herpy ridden computer "i can mask those herpes for you my sweet, with this ointment called ubuntu 8.10!"
so the owner worked for hours and hours, installing a new hard drive for the ointment to be installed onto. but there was evil afoot! for the power company didn't want to have this desktop ridden of its' herpes, and now seeing that it cannot be saved, it created a new problem... crabs(grub issues). so in the middle of the installation of the ointment the power shut off and it gave the poor desktop crabs. now this desktop was in a terrible situation, the crabs just wouldn't go away! so the owner tried his very best, and got the ointment installed on the second hard drive.
but alas, a reinstallation of the ointment didn't cure the crabs. so every time the desktop tries to load either the herpes or the ointment, crabs comes up and says "NO! YOU MAY NOT HAVE SUCH THINGS!!!" and then crabs does the most horrid thing of all, sends an error 17 report. but that's only if the ointment is loaded, if the herpes tries to load itself the crabs say "invalid windows executable!!!" (or something like that).

so the user played around with the poor little desktop for hours and hours, and found that if he puts the ointment live disc in, and tells it to boot from the first hard disc, the crabs don't come up, however, this is the only way the desktop can load its' herpes/ointment. so the owner says "hey, if i were to take the ointment back, would it still give me the same thing?", that... was a very bad mistake. so the owner removed the ointment, and now the desktop couldn't load at all. so the owner put the ointment back on, and it works the same way as it did before.

by now the poor desktop child has had enough, and she wants to know how she could just get rid of the crabs and the ointment, because she would rather just deal with the herpes that she once had before. and so here i am, the owner, asking all of you, how can i get my poor desktop to be completely rid of the crabs and ointment?

---

### Post by caljohnsmith on 2009-01-29
Well I don't think I can help with herpes or crabs, but I might be able to help you with your Grub problem. :) In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by mckinnley on 2009-01-30
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /wubildr.mbr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4c974c97

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   958,566,399   958,564,352   7 HPFS/NTFS
/dev/sda2         958,566,420   976,768,064    18,201,645   5 Extended
/dev/sda5         958,566,483   976,768,064    18,201,582  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x120a120a

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   149,838,254   149,838,192  83 Linux
/dev/sdb2         149,838,255   156,296,384     6,458,130   5 Extended
/dev/sdb5         149,838,318   156,296,384     6,458,067  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="F604428C04424FB3" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="a894e9c9-bf79-4793-9911-95da508974c9" 
/dev/sdb1: UUID="83428c70-2c9a-4f02-a027-292acb2d7ea1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="f7133d68-7812-4f40-b3ae-b0bd8be5b954" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)

=========================== sdb1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=83428c70-2c9a-4f02-a027-292acb2d7ea1 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=83428c70-2c9a-4f02-a027-292acb2d7ea1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=83428c70-2c9a-4f02-a027-292acb2d7ea1 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=83428c70-2c9a-4f02-a027-292acb2d7ea1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=f7133d68-7812-4f40-b3ae-b0bd8be5b954 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location  of files loaded by Grub: ===================


  45.7GB: boot/grub/menu.lst
  45.7GB: boot/grub/stage2
  45.7GB: boot/initrd.img-2.6.24-19-generic
  45.6GB: boot/vmlinuz-2.6.24-19-generic
  45.7GB: initrd.img
  45.6GB: vmlinuz


```

---

### Post by caljohnsmith on 2009-01-30
It looks like the issue is that you have Grub installed to the MBR (Master Boot Record) of both your drives, but your Grub's menu.lst is only configured correctly if you boot from the sdb Ubuntu drive. So to get a Grub error 17 when you boot Ubuntu means you must be booting the sda Vista drive on start up. Can you go into your BIOS and change the boot order so that your Ubuntu sdb drive boots before the Vista drive? If so, it looks like that should solve your Grub problems. How about trying that and let me know how it goes.

---

### Post by mckinnley on 2009-01-30
i'll do that, but i really wanted to just remove it entirely, because i've decided that i would rather just have the ide drive as an extra storage device. although i would guess that if that solved it i would just uninstall it the usual way.

edit: yeah that worked thanks a lot, i would have never guessed that it would be something like that

ok this is a pretty unrelated topic but i don't want to start a whole new thread on it, when i book up my vista system recovery disc it asks what opperating system that i want to fix, and there is nothing to select. the window is empty. so i'll just push next anyways to see if it works, so i get to another screen where i tell it to go to the command prompt.
from there i type in "bootrec /fixmbr" and it completes successfully, then i type in "bootrec /fixboot" and it just gets confused and says that there isn't anything to fix. so yeah, i need to get vista to boot on its' own without the support of linux

---

### Post by Yellow Pasque on 2009-01-30
Did you remember to switch the boot order of the drives back in the BIOS? This is a bit of a shot in the dark because I'm not a Windows user and I don't know how it looks for Windows installs, but it sounds like something that Windows would assume (the install is on the first disk).

---

### Post by mckinnley on 2009-01-31
yeah i tried that, it didn't work

---

### Post by caljohnsmith on 2009-01-31
If the "bootrec /fixmbr" command completed successfully, have you tried booting Vista from its own drive since then? If so, what exactly happens? I'm not sure why the Vista CD doesn't recognize your Vista install, unless maybe you have the Vista drive set as slave? Also, according to the info from the Boot Info Script, your Vista partition boot sector is fine, so there shouldn't be any need to run "bootrec /fixboot".

---

