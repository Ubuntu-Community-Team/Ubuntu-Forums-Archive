---
title: "Boot-up problem: freezes at &quot; a large Kernel ID&quot;"
date: 2009-08-27
forum: Installation &amp; Upgrades
---

### Post by tal007 on 2009-08-27
I am trying to run Ubuntu on my Desktop PC ( Spec: E5200 CPU, Gigabyte Mobo with P43 chipset ). I am able to install it successfully, yet when I try to bring it up I run into a number of problems :

1) "GRUB Loading, please wait.."

   It takes too long to get to Kernel loading stage. It is probably 3 or 4 minutes, not seconds without any exaggeration.

2) Then I see on my display "Boot from (hd0,0) ext2 + a large 
   Kernel ID"
  
   The system can never go past this point.

   I don't know what is causing it to hang there. I have installed it more that 10 times. I went on the internet and read various postings to see if anyone has run into the same problem. I tried everything conceivable to make it boot, yet the stubborn kernel adamantly refusing to boot. I am using the latest Ubuntu ( Jaunty ). I also tried Ubuntu 8.10. Still, the same problem comes up. Using the installation CD I examined the disk partitions and the system configuration files. They all looked OK. It appears to me that the Kernel the system trying to load is not meant for my system or else why would it hang there ?. I badly need your help.

Thanks.

---

### Post by stlsaint on 2009-08-27
ok are you dual booting or single boot? boot into live cd and run sudo fdisk -l...please post back here!!

---

### Post by tal007 on 2009-08-27
By the way, I am using the entire disk for Ubuntu. No other OS.
I cleaned the entire disk using a utility( e.g. zero filling utility ) , and then I installed Ubuntu on it using the "guided method". So, there can never be more than two partitions after installation. The disk was empty with no partitions on it before installation. It has been confirmed during installation by the installation script.

---

### Post by cascade9 on 2009-08-27
Zero filled? What on earth were you trying to hide? (or kill)

---

### Post by inobe on 2009-08-27
sounds like the mbr was killed, download the disk utility for that brand hard drive and use it to install the mbr, simply said the disk is dead without it.

i zeroed my drive before' that will make the disk unusable.

for seagate drives "diskwizard" maxtor "maxblast"

---

### Post by tal007 on 2009-08-27
Some kind soul on Earth please help me out. Very puzzled why kernel won't load and why it takes so long for GRUB to get to menu.lst.

---

### Post by presence1960 on 2009-08-27
Let's get a better look at your setup. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

It definitely isn't your MBR because if it were GRUB would never load. GRUB loads and appears to point to something because you should get those messages like boot from (hd0,0) ext4 and that long set of characters is the UUID. Let's see what your setup and boot process looks like before you go playing with your hard disk & MBR.

---

### Post by tal007 on 2009-08-27
Here is the info. that you have asked for. I have opened the partition editor to view the system partition table. This is 
what it displayed -


                                         used     unused   flags

/dev/sda1      ext3         18.28 GiB  2.39 GiB  15.74 GiB Boot  

/dev/sda2      extended    855.02 MiB    ----     -----

/dev/sda5      linux-swap  854.99 MiB


Very bizarre thing happed today. I installed again with a newly burned DVD. This time the system can not even get past that prompt "Grub loading, please wait..". Even after 10 minutes of waiting patiently nothing came up.   

I tried to probe the system using "/find /boot/grub/stage1" command. It points to (hd0,0). So, I tried just like others using
the following :

???$grub
grub>
grub>root (hd0,0 )
grub>setup (hd0)
grub>quit

It displays everything to be executed successfully, yet when I booted the system I could not even get past the prompt " Grub loading, please wait..". On Earth I don't know what is happening.
It appears to me that GRUB has a serious flaw in writing the MBR table. 

Folks, please share your knowledge if you happen to know anything on this problem. Shed some light, so that I can walk along the right path.

---

### Post by presence1960 on 2009-08-27
> **tal007 said:**
> Here is the info. that you have asked for. I have opened the partition editor to view the system partition table. This is 
what it displayed -


                                         used     unused   flags

/dev/sda1      ext3         18.28 GiB  2.39 GiB  15.74 GiB Boot  

/dev/sda2      extended    855.02 MiB    ----     -----

/dev/sda5      linux-swap  854.99 MiB


Very bizarre thing happed today. I installed again with a newly burned DVD. This time the system can not even get past that prompt "Grub loading, please wait..". Even after 10 minutes of waiting patiently nothing came up.   

I tried to probe the system using "/find /boot/grub/stage1" command. It points to (hd0,0). So, I tried just like others using
the following :

???$grub
grub>
grub>root (hd0,0 )
grub>setup (hd0)
grub>quit

It displays everything to be executed successfully, yet when I booted the system I could not even get past the prompt " Grub loading, please wait..". On Earth I don't know what is happening.
It appears to me that GRUB has a serious flaw in writing the MBR table. 

Folks, please share your knowledge if you happen to know anything on this problem. Shed some light, so that I can walk along the right path.

I can't help you unless you download the boot info script as I asked and run that command. I need all info about your set up & boot process. What you have provided is only a scratch on the surface.

---

### Post by tal007 on 2009-08-27
Here is further info. you have asked for. I don't know if the format got messed up. Just did a cut and paste.

Thanks

```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders, total 39876480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d65f6

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    38,122,244    38,122,182  83 Linux
/dev/sda2          38,122,245    39,873,329     1,751,085   5 Extended
/dev/sda5          38,122,308    39,873,329     1,751,022  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="f4a9fab3-0898-4a17-9ee4-af409fbc7421" TYPE="ext3" 
/dev/sda5: UUID="4daf481a-0dcf-4076-8f98-dd141a7d5c75" TYPE="swap" 

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
/dev/fd0 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sda1 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)


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
# kopt=root=UUID=f4a9fab3-0898-4a17-9ee4-af409fbc7421 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f4a9fab3-0898-4a17-9ee4-af409fbc7421

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		f4a9fab3-0898-4a17-9ee4-af409fbc7421
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=f4a9fab3-0898-4a17-9ee4-af409fbc7421 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		f4a9fab3-0898-4a17-9ee4-af409fbc7421
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=f4a9fab3-0898-4a17-9ee4-af409fbc7421 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		f4a9fab3-0898-4a17-9ee4-af409fbc7421
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

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
UUID=f4a9fab3-0898-4a17-9ee4-af409fbc7421 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=4daf481a-0dcf-4076-8f98-dd141a7d5c75 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   2.2GB: boot/grub/menu.lst
   2.2GB: boot/grub/stage2
   1.9GB: boot/initrd.img-2.6.28-11-generic
   1.9GB: boot/vmlinuz-2.6.28-11-generic
   1.9GB: initrd.img
   1.9GB: vmlinuz
```

---

### Post by presence1960 on 2009-08-27
```
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
/dev/fd0 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=9 99,utf8,umask=077,flush)
[COLOR="Red"]/dev/sda1 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)[/COLOR]
```

This here may be your problem in red. You created a mountpoint for sda1 when it automounts anyway at boot or did you mount that after you booted the Live CD? If you didn't mount it after you booted the Live Cd that is a problem. I checked this against my boot info scripts from my 7 year old daughter's machine and mine. There is no mount point for / in /media. I would look into that. here is another potential problem:

> =============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=f4a9fab3-0898-4a17-9ee4-af409fbc7421 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=4daf481a-0dcf-4076-8f98-dd141a7d5c75 none            swap    sw              0       0
[COLOR="Red"]/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0[/COLOR]

I have a floppy and DVD-RAM drives and have never had them in fstab as they will auto mount when you insert media. I know it says noauto in the lines but there really is no reason for those lines to be there.

Other than those 2 things everything else looks ok!

FYI whenever you are posting a lot of text, highlight the text and click the #sign on the toolbar to place code tags around the text. This way it doesn't take up a whole page.

---

### Post by tal007 on 2009-08-28
As a matter of fact, I inserted the floppy during boot time that's why it showed up. As for other thing, you are right, I placed it on the my Desktop by dragging it from the tool bar menu. But again, later I tried differently. By bringing up the system using the Live CD and then mounting it on a directory and executing the following commands. 

??$ sudo mount /dev1/sda1 /tmp
??$ cd /tmp/boot/grub

sudo grub
grub> root (hd0,0 )
grub> setup(hd0)
grub> quit
grub> exit

??$sudo umount /dev/sda1

Still, I am stuck and can not proceed any further than the following prompt "Grub load, please wait..".

---

### Post by Bartender on 2009-08-28
I'm wondering if his download was corrupted, or maybe he burned the disc at ludicrous speed?
Also, the OP mentioned using a DVD - thought I've seen posts that claimed using a DVD instead of a CD-R doesn't work?

---

