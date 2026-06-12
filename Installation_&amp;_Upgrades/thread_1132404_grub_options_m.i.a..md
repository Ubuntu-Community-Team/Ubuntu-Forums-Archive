---
title: "grub options m.i.a."
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by Rita G. on 2009-04-21
just installed kubuntu 9.04. 

have 2 other operating systems on hard drive, but grub does not see them.....

so it will only boot kubuntu 9.04.

the os's were not deleted in the installation; gparted shows them intact.

how can i get them on grub menu???

---

### Post by meierfra. on 2009-04-21
Since Kubuntu should have detected the other OS's (or did you unplug some of the  hard drives?), I think it is best to have a closer look at  your setup. Boot into Ubuntu  and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by Rita G. on 2009-04-22
after a dban & re-partition,

tried to mount systems again with no success regarding grub.

results.txt
[CODE============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu jaunty (development 
                       branch)
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda8: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda9: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda10: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda11: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda12: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Debian GNU/Linux 5.0
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009fc82

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   156,296,384   156,296,322   5 Extended
/dev/sda5                 126    11,566,799    11,566,674  82 Linux swap / Solaris
/dev/sda6          24,884,748    42,491,924    17,607,177  83 Linux
/dev/sda7          42,491,988    60,934,544    18,442,557  83 Linux
/dev/sda8          60,934,608    82,670,489    21,735,882  83 Linux
/dev/sda9          82,670,553   107,105,354    24,434,802  83 Linux
/dev/sda10        107,105,418   131,700,869    24,595,452  83 Linux
/dev/sda11        131,700,933   156,296,384    24,595,452  83 Linux
/dev/sda12   *     11,566,863    24,884,684    13,317,822  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda5: UUID="648fa06a-2898-4bb4-9455-08794e6d3e8e" TYPE="swap" 
/dev/sda6: UUID="7efea393-9a93-40fb-a9dc-5c8bca2f658e" TYPE="ext3" 
/dev/sda12: UUID="7b970bdb-3074-4b85-98b7-01a93cc3c6de" TYPE="reiserfs" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
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


=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=7efea393-9a93-40fb-a9dc-5c8bca2f658e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7efea393-9a93-40fb-a9dc-5c8bca2f658e

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

title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic
uuid		7efea393-9a93-40fb-a9dc-5c8bca2f658e
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7efea393-9a93-40fb-a9dc-5c8bca2f658e ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic (recovery mode)
uuid		7efea393-9a93-40fb-a9dc-5c8bca2f658e
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7efea393-9a93-40fb-a9dc-5c8bca2f658e ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu jaunty (development branch), memtest86+
uuid		7efea393-9a93-40fb-a9dc-5c8bca2f658e
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=7efea393-9a93-40fb-a9dc-5c8bca2f658e /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=648fa06a-2898-4bb4-9455-08794e6d3e8e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  15.0GB: boot/grub/menu.lst
  15.0GB: boot/grub/stage2
  12.7GB: boot/initrd.img-2.6.28-11-generic
  21.6GB: boot/vmlinuz-2.6.28-11-generic
  12.7GB: initrd.img
  21.6GB: vmlinuz

========================== sda12/boot/grub/menu.lst: ==========================

# See www.gnu.org/software/grub for details
# By default, boot the first entry
default 0
# Boot automatically after 5 seconds
timeout 25
gfxmenu /boot/grub/message.elive

title Elive Gem+ 
root (hd0,11)
kernel /boot/vmlinuz-2.6.26.8-elive-686 root=UUID=7b970bdb-3074-4b85-98b7-01a93cc3c6de vga=791 splash=silent resume=UUID=648fa06a-2898-4bb4-9455-08794e6d3e8e
initrd /boot/initrd.img-2.6.26.8-elive-686

title 		Memory RAM diagnostic
root		(hd0,11)
kernel	 	/boot/memtest86+.bin
savedefault
boot


=============================== sda12/etc/fstab: ===============================

# Generated by Elive

proc		/proc	proc		defaults	0	0
sysfs		/sys	sysfs		defaults	0	0
UUID=648fa06a-2898-4bb4-9455-08794e6d3e8e	none	swap		sw	0	0
UUID=7b970bdb-3074-4b85-98b7-01a93cc3c6de	/	reiserfs	defaults	0	1
/dev/sda10	/mnt/sda10	auto    defaults,auto        0       2
/dev/sda11	/mnt/sda11	auto    defaults,auto        0       2
/dev/sda6	/mnt/sda6	auto    defaults,auto        0       2
/dev/sda7	/mnt/sda7	auto    defaults,auto        0       2
/dev/sda8	/mnt/sda8	auto    defaults,auto        0       2
/dev/sda9	/mnt/sda9	auto    defaults,auto        0       2

=================== sda12: Location of files loaded by Grub: ===================


   5.9GB: boot/grub/menu.lst
  12.6GB: boot/grub/stage2
   6.0GB: boot/initrd.img-2.6.26.8-elive-686
   5.9GB: boot/initrd.img-2.6.26.8-elive-686.sig
   6.0GB: boot/vmlinuz
   6.0GB: boot/vmlinuz-2.6.26.8-elive-686
   6.0GB: initrd.img
   6.0GB: vmlinuz
   6.0GB: vmlinuz-2.6.26.8-elive-686
CODE]

---

### Post by meierfra. on 2009-04-22
There seems to be something wrong with the partitions  sda7 to sda11.
The script was not able to mount them, and "blkid" does not list them.
What's on those partitions?


I don't know why Ubuntu did not detect your "Elive Gem".
I suggest to chainload it:

Install grub to the boot sector of /dev/sda12

```
sudo grub
```
and at the "grub>" prompt:

```
root (hd0,11)
setup (hd0,11)
quit
```

You also need to edit the Ubuntu  menu.lst:

```
gksudo gedit /boot/grub/menu.lst
```

add this to the very end of the file"

title Elive Gem
root (hd0,11)
chainloader +1


Once you  booted into Elive Gem, you might want to edit  your "Elive Gem" menu.lst so that you don't have to go through to boot menu:

Change "timeout  25" to "timeout 2" and add "hiddenmenu".

---

### Post by Rita G. on 2009-04-22
thank you very much meierfra for all your help & patience.

we're making progress!

how do i 

change "timemout 24" to "timeout 2" and add "hiddenmenu".

---

### Post by meierfra. on 2009-04-22
> change "timemout 24" to "timeout 2" and add "hiddenmenu". 

I meant "timeout 25" and not "timemout 24". 

Anyway, boot into Elive Gem and open menu.lst via

```
gksudo gedit /boot/grub/menu.lst
```

Change 

timeout 25
gfxmenu /boot/grub/message.elive

to

timeout 2
#gfxmenu /boot/grub/message.elive
hiddenmenu

---

### Post by Rita G. on 2009-04-22
after the fixes you gave me i was able to boot both systems.

now after installing 3rd system, grub has other systems on menu, but will not boot either one.

what kind of problem is this?

i've never had this happen before....they are all grub defective!

do i need a new hard drive or mobo or what?

---

### Post by meierfra. on 2009-04-22
> what kind of problem is this?

Could you run the boot_info_script  and post "RESULTS.txt" again?

---

### Post by Rita G. on 2009-04-22
been playing with boot_info_script032.sh (& cooking dinner) on 3rd system for hours & can't get it to work.

in the meantime, i'm gonna run a hdd diagnostic on it.

will try boot_info_script032.sh later & report.

---

### Post by Rita G. on 2009-04-22
using DLGDIAG 5.04f &#8211; Data Lifeguard Diagnostics

1st test had to abort &#8211; overtemp!

put a  fan (about 3.5&#8221; dia.) from another box in front of hdd.

2nd test - 6 min. quick test  completed w/o errors.

3rd test &#8211; 20 min. extended test completed w/o errors.

could this box have been running screwy due to heat?

will try the boot info script again tomorrow & report back.

---

### Post by Rita G. on 2009-04-23
aha.............

just installed 4th system and ALL 4 grub entries on menu function normally!

could heat have been the killer here, or am i arriving at a hasty conclusion?

---

### Post by meierfra. on 2009-04-23
> just installed 4th system and ALL 4 grub entries on menu function normally!

could heat have been the killer here, or am i arriving at a hasty conclusion?

I'm not sure. The 4th system might just have done a better job setting up grub.

---

