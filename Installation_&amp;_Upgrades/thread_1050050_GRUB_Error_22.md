---
title: "GRUB Error 22"
date: 2009-01-25
forum: Installation &amp; Upgrades
---

### Post by notwen on 2009-01-25
Long story short, I had a hard drive go bad on me, not containing my Ubuntu install.  I replaced the hdd, moved my install to a different hdd and GRUB greets me w/ an Error 22.  I've posted my fstab and menu.lst, please let me know if you need any additional info.

**/etc/fstab**
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=ffe5a265-e3a6-495f-a509-d3a4aa2a92af /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=b3c77291-7277-4b9f-9400-e5a85eb7b410 /home           ext3    relatime        0       2
# /dev/sda2
UUID=a842d110-1a63-4e41-a278-ed2f63b0b1c7 /media/sda      ext3    relatime        0       2
# /dev/sdb2
UUID=6dafc37e-a2ca-4e9d-ae62-1e0414bb0201 /media/sdb      ext3    relatime        0       2
# /dev/sdc1
UUID=252de369-930f-404f-9241-d220db2a5fe2 /media/sdc      ext3    relatime        0       2
# /dev/sda7
UUID=c60f3cd0-3652-40b5-aa21-ca54dd3402cf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/fd1        /media/floppy1  auto    rw,user,noauto,exec,utf8 0       0

```

**menu.lst**
```

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
# kopt=root=UUID=ffe5a265-e3a6-495f-a509-d3a4aa2a92af ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ffe5a265-e3a6-495f-a509-d3a4aa2a92af ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ffe5a265-e3a6-495f-a509-d3a4aa2a92af ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by Pumalite on 2009-01-25
Boot your Live CD, go to the Terminal:
```
sudo grub
find /boot/grub/stage1
root (?,?)
setup (hdo)

```
Reboot.

---

### Post by caljohnsmith on 2009-01-25
In order to get a clearer picture of your setup related to your booting problem, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

### Post by notwen on 2009-01-25
> **Pumalite said:**
> Boot your Live CD, go to the Terminal:
```
sudo grub
find /boot/grub/stage1
root (?,?)
setup (hdo)

```
Reboot.

After doing this, I am still getting the Error 22.

> 
Booting from local disk...
GRUB loading stage1.5.


GRUB loading, please wait...
Error 22


---

### Post by notwen on 2009-01-25
> **caljohnsmith said:**
> In order to get a clearer picture of your setup related to your booting problem, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

Here are is the output from your script:

```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     
    Operating System:  Ubuntu 8.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000bb725

Partition  Boot        Start          End         Size  Id System

/dev/sda1    *            63   46,668,824   46,668,762   5 Extended
/dev/sda5                126   20,964,824   20,964,699  83 Linux
/dev/sda6         20,964,888   41,929,649   20,964,762  83 Linux
/dev/sda7         41,929,713   46,668,824    4,739,112  82 Linux swap / Solaris
/dev/sda2         46,668,8251,953,520,0641,906,851,240  83 Linux


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00058efc

Partition  Boot        Start          End         Size  Id System

/dev/sdb2                 63  390,716,864  390,716,802  83 Linux


Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x01c3ba1b

Partition  Boot        Start          End         Size  Id System

/dev/sdc1                 63  586,099,394  586,099,332  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda2: UUID="a842d110-1a63-4e41-a278-ed2f63b0b1c7" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="ffe5a265-e3a6-495f-a509-d3a4aa2a92af" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="b3c77291-7277-4b9f-9400-e5a85eb7b410" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="c60f3cd0-3652-40b5-aa21-ca54dd3402cf" 
/dev/sdb2: UUID="6dafc37e-a2ca-4e9d-ae62-1e0414bb0201" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="252de369-930f-404f-9241-d220db2a5fe2" SEC_TYPE="ext2" TYPE="ext3" 
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
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

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
# kopt=root=UUID=ffe5a265-e3a6-495f-a509-d3a4aa2a92af ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ffe5a265-e3a6-495f-a509-d3a4aa2a92af ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ffe5a265-e3a6-495f-a509-d3a4aa2a92af ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=ffe5a265-e3a6-495f-a509-d3a4aa2a92af /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=b3c77291-7277-4b9f-9400-e5a85eb7b410 /home           ext3    relatime        0       2
# /dev/sda2
UUID=a842d110-1a63-4e41-a278-ed2f63b0b1c7 /media/sda      ext3    relatime        0       2
# /dev/sdb2
UUID=6dafc37e-a2ca-4e9d-ae62-1e0414bb0201 /media/sdb      ext3    relatime        0       2
# /dev/sdc1
UUID=252de369-930f-404f-9241-d220db2a5fe2 /media/sdc      ext3    relatime        0       2
# /dev/sda7
UUID=c60f3cd0-3652-40b5-aa21-ca54dd3402cf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/fd1        /media/floppy1  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location  of files loaded by Grub: ===================


   9.3GB: boot/grub/menu.lst
   9.2GB: boot/grub/stage2
   9.3GB: boot/initrd.img-2.6.24-16-generic
   9.3GB: boot/initrd.img-2.6.24-16-generic.bak
   9.3GB: boot/vmlinuz-2.6.24-16-generic
   9.3GB: initrd.img
   9.3GB: vmlinuz

=============================== StdErr Messages: ===============================

No errors were reported.

```

---

### Post by Pumalite on 2009-01-25
[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)

---

### Post by caljohnsmith on 2009-01-25
It looks like the problem is that you have Grub installed to the MBR (Master Boot Record) of all your drives at present. If you can go into your BIOS and make sure the sda Ubuntu drive is being booted before your other drives (sda should be first in the BIOS boot order), it looks like you should be able to boot into Ubuntu without any problems. How about trying that and let me know how it goes.

---

### Post by notwen on 2009-02-09
I've tried all of my HDDs as the first startup device in my BIOS and still getting Error 22.  Is there anyway to just plain remove the MBR from all drives?  I've backed up all my data and would like to just get my machine back up & running.  I'm going to try to run DBAN this Friday and try a re-install once again unless you guys can come up w/ another recommendation.  Any thoughts?  =]

---

### Post by caljohnsmith on 2009-02-09
OK, how about we remove Grub from the MBR of all your drives except the Ubuntu drive, and then it will be clear when you are booting the Ubuntu drive. To do that, boot your Live CD again, open a terminal and do:
```
sudo apt-get install lilo
sudo lilo -M /dev/sdb mbr
sudo lilo -M /dev/sdc mbr
```
Next, I think it would be good to disable the "hiddenmenu" option in your Grub's menu.lst in order to make it clear if you successfully get the Grub menu on start up:
```
sudo mount /dev/sda1 /mnt && gksudo gedit /mnt/boot/grub/menu.lst
```
And then put a pound/hash sign "#" in front of the "hiddenmenu" line:
```
# hiddenmenu
```
then reboot, set your BIOS to boot the sda Ubuntu drive, and let me know how far you get this time.

---

### Post by notwen on 2009-02-09
> **caljohnsmith said:**
> then reboot, set your BIOS to boot the sda Ubuntu drive, and let me know how far you get this time.

Just to make sure we're on the same page and I'm doing exactly what you request, is there anyway to determine which HDD-X in BIOS settings is my sda drive in Linux/GRUB ? =]

---

### Post by caljohnsmith on 2009-02-09
> **notwen said:**
> Just to make sure we're on the same page and I'm doing exactly what you request, is there anyway to determine which HDD-X in BIOS settings is my sda drive in Linux/GRUB ? =]
I'm not sure what you mean? If you mean when you try to set the BIOS boot order to boot the sda Ubuntu drive first, I don't know how your BIOS will identify the Ubuntu drive. If your BIOS gives any info about the drives, you could just look for your 1 TB drive, and that will be the Ubuntu drive. If you do those commands I gave to remove Grub from your other drives, it will be clear once you have your BIOS set to boot the Ubuntu drive, because your other drives won't give you a Grub menu or Grub error on start up. Instead you will probably get an "operating system not found" type error.

---

### Post by Grogger on 2009-02-09
Thanks guys for helping me sort through my grub error by reading this thread.  I found that my BIOS boot order just needed to be adjusted to enter my new intrepid install.  Good luck at working toward a solution.

---

