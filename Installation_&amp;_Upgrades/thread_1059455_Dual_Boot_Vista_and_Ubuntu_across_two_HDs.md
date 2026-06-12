---
title: "Dual Boot Vista and Ubuntu across two HDs"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by Bob Smith on 2009-02-03
i know i know, this has been asked a million times before, but i still haven't found the answers to my specific problems so please help.

i have 2 hds, one a 250 gb for Ubuntu and a 1.5 TB for vista, but vista doesn't show up in my bootloader or menu.lst file. I installed Ubuntu secondly, but did not erase vista, i can even access the files from Ubuntu. What I can't do is boot it because it's not on the bootloader yet. please help.

---

### Post by easybake on 2009-02-03
You have to edit your grub menu to add vista to the bootloader. 
```
sudo gedit /boot/grub/menu.lst
```

You can copy one of the examples in the menu file but change the root line to (hd1,0)

---

### Post by Bob Smith on 2009-02-03
that what i thought, but it isn't working.

everytime i click vista it just restarts the computer. i think it's not going to the right hd, or at least not the right location which doesn't make sense so i'm probably wrong.

---

### Post by caljohnsmith on 2009-02-03
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by Bob Smith on 2009-02-03
> **caljohnsmith said:**
> In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x45c845c7

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   471,684,464   471,684,402  83 Linux
/dev/sda2         471,684,465   488,392,064    16,707,600   5 Extended
/dev/sda5         471,684,528   488,392,064    16,707,537  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e3e7a

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048 2,930,274,303 2,930,272,256   7 HPFS/NTFS

/dev/sdb1 ends after the last cylinder of /dev/sdb

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="96959348-866e-4f1d-b940-006cb3cb07e1" TYPE="ext3" 
/dev/sda5: UUID="a7a3a3b6-9a4b-4eec-a686-7ab3f36952cb" TYPE="swap" 
/dev/sdb1: UUID="A6F46886F4685A97" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/orval/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=orval)

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
timeout		30

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)

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

 title		Vista
 root		(hd1,0)
 makeactive
 chainloader	+1

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
# kopt=root=UUID=96959348-866e-4f1d-b940-006cb3cb07e1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=96959348-866e-4f1d-b940-006cb3cb07e1

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

title		Ubuntu
uuid		96959348-866e-4f1d-b940-006cb3cb07e1
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=96959348-866e-4f1d-b940-006cb3cb07e1 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=96959348-866e-4f1d-b940-006cb3cb07e1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=a7a3a3b6-9a4b-4eec-a686-7ab3f36952cb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 152.0GB: boot/grub/menu.lst
 151.9GB: boot/grub/stage2
 151.9GB: boot/initrd.img-2.6.27-11-generic
 151.9GB: boot/initrd.img-2.6.27-7-generic
 151.9GB: boot/vmlinuz-2.6.27-11-generic
 151.9GB: boot/vmlinuz-2.6.27-7-generic
 151.9GB: initrd.img
 151.9GB: initrd.img.old
 151.9GB: vmlinuz
 151.9GB: vmlinuz.old

```

---

### Post by Bob Smith on 2009-02-03
by the way, this isn't my computer it's my grandads. thats why i removed the other Ubuntu boot options from the Grub file and increased the timeout, i wanted to make it easy for him.

also, we have a 500gb external hd, but it's blank right now.

---

### Post by caljohnsmith on 2009-02-03
It looks like the problem is your Vista partition is missing its boot files. Did you have an NTFS/FAT partition on your sda drive that you deleted when you installed Ubuntu? If so, that is probably where Vista put its boot files. I would suggest following step 2 of [this tutorial]("http://ubuntuforums.org/showpost.php?p=5726832") in order to restore your Vista boot files. Note you don't have to run the last "bootsect" command in step 2 of that tutorial, because according to the script output your Vista boot sector appears to be fine. And lastly, I would recommend using the following entry for Vista in your Grub's menu.lst:
```
title Windows Vista
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Let me know how it goes or if you run into problems.

---

### Post by Bob Smith on 2009-02-03
thx. it work, but right after i finished my grandad made the realization that the software he wanted to run on windows (xplane) works on ubuntu so my 2.5 hours of work and 0.5 hours of begging him not to use windows (i'm a mac/ubuntu man) were all in vain.

would it make me a bad person if i popped in a copy of puppy linux, hit restart and left his computer crippled out of spite?

---

