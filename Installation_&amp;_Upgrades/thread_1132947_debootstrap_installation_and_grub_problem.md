---
title: "debootstrap installation and grub problem"
date: 2009-04-22
forum: Installation &amp; Upgrades
---

### Post by meg23 on 2009-04-22
I installed ubuntu using debootstrap onto an external hard drive intended to be used as an internal hard drive. After installing the hard drive into the computer and rebooting it, I get a Grub prompt with a flashing underscore (Grub_) and no ability to drop into a shell. I figure my problem must be either with my menu.lst, device.map, or my fstab. Here is some information:

sda is my internal laptop drive
sdc is my external drive meant to be installed in another computer

df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              71G   42G   26G  62% /
varrun                632M  136K  632M   1% /var/run
varlock               632M     0  632M   0% /var/lock
udev                  632M   56K  632M   1% /dev
devshm                632M     0  632M   0% /dev/shm
lrm                   632M   39M  593M   7% /lib/modules/2.6.24-23-generic/volatile
gvfs-fuse-daemon       71G   42G   26G  62% /home/moshe/.gvfs
/dev/sdb1             748M  289M  422M  41% /mnt/installer
/dev/sdc1             748M  289M  422M  41% /media/disk

sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f800100

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdc: 6488 MB, 6488294400 bytes
255 heads, 63 sectors/track, 788 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007f1e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1          96      771088+  83  Linux

Here is my menu.lst minus the default stuff:

title installer1
root (hd0,0)
kernel /boot/newinstall/vmlinuz
initrd /boot/newinstall/initrd.gz

here is my device map:

(fd0)	/dev/fd0
(hd0)   /dev/sda

here is my fstab:

# UNCONFIGURED FSTAB FOR BASE SYSTEM
/dev/hda1 	/ 	ext2 	defaults 	1 1
/dev/hdb1 	/home 	ext2 	defaults 	1 2
/dev/cdrom 	/media/cdrom 	auto 	ro,noauto,user,exec 	0 0
/dev/fd0 	/media/floppy 	auto 	rw,noauto,user,sync 	0 0
proc 	/proc 	proc 	defaults 	0 0
/dev/hda1 	swap 	swap 	pri=42 	0 0

I would really appreciate if someone who has attempted this before knew how to get grub to boot the install.

---

### Post by meierfra. on 2009-04-22
Booting to the"Grub>" prompt is pretty unusual. So to figure out what is causing the problem, I'll need some more information:

Are you able to type at the  "Grub>" prompt. If yes, what is the output of

```
find /boot/grub/stage2

find /boot/grub/menu.lst

find /vmlinuz
```

Also type

```
geometry (hd0)
geometry (hd1)
geometry (hd2)
```

This should list the partitions on each of your hard drives.  Are all you hard drives detected?   Which one is which?

I also  suggest to boot  from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post. (Use the code tags)

---

### Post by meg23 on 2009-04-22
Its not really a boot prompt. It looks like grub is looking for something to load. The external hard drive is /dev/sdc.

Here is the RESULTS.txt 
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on boot drive #1 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0f800100

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   149,838,254   149,838,192  83 Linux
/dev/sda2         149,838,255   156,296,384     6,458,130   5 Extended
/dev/sda5         149,838,318   156,296,384     6,458,067  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 6488 MB, 6488294400 bytes
255 heads, 63 sectors/track, 788 cylinders, total 12672450 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0007f1e0

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63     1,542,239     1,542,177  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="f61404d9-aa78-4839-8993-12a56eb318ef" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="b5adf34e-df71-4938-9784-ad6509b98b74" 
/dev/sdc1: UUID="0ab1008a-7db3-4687-8773-23399d802b7b" TYPE="ext2" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/moshe/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=moshe)
/dev/sdb1 on /mnt/installer type ext2 (rw)
/dev/sdc1 on /media/disk type ext2 (rw,nosuid,nodev,uhelper=hal)


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
# kopt=root=UUID=f61404d9-aa78-4839-8993-12a56eb318ef ro

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=f61404d9-aa78-4839-8993-12a56eb318ef ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=f61404d9-aa78-4839-8993-12a56eb318ef ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=f61404d9-aa78-4839-8993-12a56eb318ef ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=f61404d9-aa78-4839-8993-12a56eb318ef ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=f61404d9-aa78-4839-8993-12a56eb318ef ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=f61404d9-aa78-4839-8993-12a56eb318ef ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f61404d9-aa78-4839-8993-12a56eb318ef ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f61404d9-aa78-4839-8993-12a56eb318ef ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f61404d9-aa78-4839-8993-12a56eb318ef /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=b5adf34e-df71-4938-9784-ad6509b98b74 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  45.1GB: boot/grub/menu.lst
  61.6GB: boot/grub/stage2
  60.0GB: boot/initrd.img-2.6.24-19-generic
  60.0GB: boot/initrd.img-2.6.24-19-generic.bak
   2.1GB: boot/initrd.img-2.6.24-21-generic
  60.0GB: boot/initrd.img-2.6.24-21-generic.bak
  60.0GB: boot/initrd.img-2.6.24-22-generic
  60.0GB: boot/initrd.img-2.6.24-22-generic.bak
  44.7GB: boot/initrd.img-2.6.24-23-generic
  61.8GB: boot/initrd.img-2.6.24-23-generic.bak
  60.0GB: boot/vmlinuz-2.6.24-19-generic
  60.0GB: boot/vmlinuz-2.6.24-21-generic
  60.0GB: boot/vmlinuz-2.6.24-22-generic
  44.3GB: boot/vmlinuz-2.6.24-23-generic
  44.7GB: initrd.img.old
  44.3GB: vmlinuz.old

=========================== sdc1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
# grub-install(8), grub-floppy(8),
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
# hiddenmenu

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## ## End Default Options ##

title installer1
root (hd0,0)
kernel /boot/newinstall/vmlinuz
initrd /boot/newinstall/initrd.gz



=============================== sdc1/etc/fstab: ===============================

# UNCONFIGURED FSTAB FOR BASE SYSTEM
/dev/hda1 	/ 	ext2 	defaults 	1 1
/dev/hdb1 	/home 	ext2 	defaults 	1 2
/dev/cdrom 	/media/cdrom 	auto 	ro,noauto,user,exec 	0 0
/dev/fd0 	/media/floppy 	auto 	rw,noauto,user,sync 	0 0
proc 	/proc 	proc 	defaults 	0 0
/dev/hda1 	swap 	swap 	pri=42 	0 0

=================== sdc1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/menu.lst
    .1GB: boot/initrd.img-2.6.24-16-generic
    .1GB: boot/vmlinuz-2.6.24-16-generic
    .1GB: initrd.img
    .1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2



=============================== StdErr Messages: ===============================

hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
```

---

### Post by meg23 on 2009-04-22
I just noticed something /dev/sdc1 should be Ext 3 right?

---

### Post by meierfra. on 2009-04-22
> I just noticed something /dev/sdc1 should be Ext 3 right? 
ext2 should be fine, too.


> =================== sdc1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/menu.lst
    .1GB: boot/initrd.img-2.6.24-16-generic
    .1GB: boot/vmlinuz-2.6.24-16-generic
    .1GB: initrd.img
    .1GB: vmlinuz


Your problem is that "/boot/grub/stage2" is missing. (Stage2 is the main part of the Grub)

Did you get any error messages during the installation?  

Am I right that  you are able to boot into the Ubuntu on /dev/sda1 by setting the bios to boot from the internal drive?

If yes, try this

Boot into Ubuntu on /dev/sda1 and open menu.lst
via

```
 gksudo gedit /boot/grub/menu.lst
```


Add


title installer1  (hd1)
root (hd1,0)
kernel /boot/newinstall/vmlinuz
initrd /boot/newinstall/initrd.gz


title installer1  (hd2)
root (hd2,0)
kernel /boot/newinstall/vmlinuz
initrd /boot/newinstall/initrd.gz

to the very end of the file.

Reboot and press "esc" during the "321" countdown to bring up the Grub menu.

Then try both  of the new entries and see whether the installation completes.

---

### Post by meg23 on 2009-04-22
I think you might a little confused with my setup. This is what I have:

Laptop (connected to internal Hard drive of Pentium 2)

Pentium 2 Desktop 

I am trying to install ubuntu on internal hard drive (ide) into the Pentium 2 because it does not have a floppy or a cd drive. I am merely using the laptop to install the OS to the hard drive. 

When I put the hard drive into the Pentium 2, I get Grub _ , blinking and not doing anything and no prompting. 

When I put the hard drive into the Pentium 2, does the BIO see it as hd0,0 because it is the only disk?

Anyways, I tried editing the menu.lst the way you suggested as well adding some extra ones, but no avail. 

I tried to install stage 2 but I get this error on the laptop:

```
sudo setup  --stage2=/boot/grub/stage2 --prefix=/boot/grub (hd1,0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,0)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "install --stage2=/boot/grub/stage2 /boot/grub/stage1 d (hd1,0) /boot/grub/stage2 p /boot/grub/menu.lst "... failed

Error 21: Selected disk does not exist
```

Thanks for your help. I am freakin' pretty determined to do this.

---

### Post by meierfra. on 2009-04-23
> you might a little confused with my setup. 
I thought you were just switching the boot order in the bios of the laptop  to boot from the Pentium 2 drive. Instead,  you plugged the Pentium 2 drive back into  Pentium 2 desktop. 
But I don't think that really matters.


> When I put the hard drive into the Pentium 2, does the BIO see it as hd0,0 because it is the only disk?
Yes.



> Anyways, I tried editing the menu.lst the way you suggested as well adding some extra ones, but no avail.

What exactly did you try?  I wanted you to edit the menu.lst on the hard drive of the  laptop. Then boot from the laptop, while the Pentium 2 hard drive is attached to the laptop, and see what happens if you pick one of added entries at the Grub menu. 


> Error 21: Selected disk does not exist

Your pentium 2 hard drive is /dev/sdc, which makes it (hd2).   For some reason you have /dev/sda and /dev/sdc, but no /dev/sdb. So (hd1) does not exist, giving you Grub error 21.
But the setup command does not install "stage2". So you won't be able to solve your problem this way.

> => Grub0.97 is installed in the MBR of /dev/sdc and looks on boot drive #1 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

I'm a little puzzled about this part of RESULTS.txt. Before you ran the boot_info_script, did you already try to install grub to the MBR of the Pentium drive? Say via the "setup" command?


Try this, (with the Pentium 2 drive attached to the laptop)
```
sudo mount /dev/sdc1 /mnt
sudo cp /boot/grub/stage2 /mnt/boot/grub/stage2
```
Then plug the Pentium 2 drive back in the Pentium 2, and see whether you can boot.

---

### Post by meg23 on 2009-04-27
I just got back home to try what you suggested. I formatted the disk and did the whole thing again, trying to install stage 2 on the external disk, but every time I get the same Grub_ . Thanks for your help but I am just going to have to find another way.

---

