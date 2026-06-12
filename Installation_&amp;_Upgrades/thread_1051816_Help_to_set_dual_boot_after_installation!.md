---
title: "Help to set dual boot after installation!"
date: 2009-01-27
forum: Installation &amp; Upgrades
---

### Post by oleksus on 2009-01-27
Hello fellow Ubuntu ppl!

I've just installed Ubuntu Studio using alternate DVD.

I have two hard disks, one of which is used for WinXP and another is now hosting Ubuntu (installed with 'use entire disk' option).

But now when I boot up my Grub doesn't show any 'other operating systems' option! So, I can't boot into WinXP, which is on the second hard drive.

I wonder, how can I set this booting option up manually, from within Grub or Ubuntu?

---

### Post by theApokalypsis on 2009-01-27
Hey,

I have Vista running on a separate HD. If you:

sudo gedit /boot/grub/menu.lst

There are included comments that give an example of putting in another Vista/XP entry that boots from a specified drive. I posted below what my file looks like for reference. HD names might differ.

I excluded all the comments/examples

```

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		c3c38747-5dfd-4dce-880e-2cce654276f6
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=c3c38747-5dfd-4dce-880e-2cce654276f6 ro splash quiet 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		c3c38747-5dfd-4dce-880e-2cce654276f6
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=c3c38747-5dfd-4dce-880e-2cce654276f6 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Jaunty Jacalope 9.04 (Alpha1)
uuid		bcb1b18a-a794-421c-bdd2-ce3aa4d26ece
root 		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=bcb1b18a-a794-421c-bdd2-ce3aa4d26ece ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Jaunty Jacalope 9.04 (Alpha1) (recovery mode)
uuid		bcb1b18a-a794-421c-bdd2-ce3aa4d26ece
root 		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=bcb1b18a-a794-421c-bdd2-ce3aa4d26ece ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Windows Vista
root		(hd1,0)
makeactive
chainloader	+1
quiet

```

hope this helps.

:-)

---

### Post by oleksus on 2009-01-27
Well, I tried to insert the lines 
```

title		Windows XP
root		(hd1,0)
makeactive
chainloader	+1
quiet
```

At the startup it just prompted 'STARTING UP...' and nothing happened.

Guess I should write the proper line instead of (hd1,0).
I have two 40gb hard drives, on one of which WinXP is located. 
How can I check the proper name for it?

---

### Post by euchrid33 on 2009-01-27
I have a similar problem.  I have Ubuntu and XP on the same drive, on separate partitions.  I reinstalled GRUB after installing XP (because of course it overwrites the MBR) but there's no GRUB entry for XP now.  I'm fine to write it in, I just need to know how to find the correct address for it.

---

### Post by caljohnsmith on 2009-01-27
Oleksus, how about instead trying:
```
title		Windows XP
root	(hd1,0)
map     (hd0) (hd1)
map     (hd1) (hd0)
chainloader +1
```
Let me know if that works or not.

---

### Post by oleksus on 2009-01-27
I tried what you suggested, it sayd 'NTLDR is absent' on boot prompt.
Can it be (hd2) that I must write?

---

### Post by caljohnsmith on 2009-01-27
OK, in order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by oleksus on 2009-01-27
ok, I ran the script, here are the RESULTS

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Lilo is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     
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
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     
    Operating System:  Windows XP
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Boot file info:     
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders, total 78242976 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb356aa4a

Partition  Boot        Start          End         Size  Id System

/dev/sda1    *            63   74,943,224   74,943,162  83 Linux
/dev/sda2         74,943,225   78,236,549    3,293,325   5 Extended
/dev/sda5         74,943,288   78,236,549    3,293,262  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders, total 156368016 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x42134213

Partition  Boot        Start          End         Size  Id System

/dev/sdb1    *            63   78,124,094   78,124,032   7 HPFS/NTFS
/dev/sdb2         78,124,095  156,280,319   78,156,225   f W95 Ext'd (LBA)
/dev/sdb5         78,124,158  156,280,319   78,156,162   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="c60e7d99-8e0b-4a42-aff2-fb3127c43f0b" TYPE="ext3" 
/dev/sda5: UUID="06f85f2d-11dd-4161-8f32-3f6eb529ff8d" TYPE="swap" 
/dev/sdb1: UUID="4C982C5A982C4534" TYPE="ntfs" 
/dev/sdb5: UUID="C45CCEBE5CCEAA8E" TYPE="ntfs" 

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
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/oleksus/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=oleksus)
/dev/scd1 on /media/cdrom0 type udf (ro,nosuid,nodev,utf8,user=oleksus)

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
# kopt=root=UUID=c60e7d99-8e0b-4a42-aff2-fb3127c43f0b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c60e7d99-8e0b-4a42-aff2-fb3127c43f0b

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		c60e7d99-8e0b-4a42-aff2-fb3127c43f0b
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=c60e7d99-8e0b-4a42-aff2-fb3127c43f0b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		c60e7d99-8e0b-4a42-aff2-fb3127c43f0b
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=c60e7d99-8e0b-4a42-aff2-fb3127c43f0b ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		c60e7d99-8e0b-4a42-aff2-fb3127c43f0b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c60e7d99-8e0b-4a42-aff2-fb3127c43f0b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		c60e7d99-8e0b-4a42-aff2-fb3127c43f0b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c60e7d99-8e0b-4a42-aff2-fb3127c43f0b ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		c60e7d99-8e0b-4a42-aff2-fb3127c43f0b
kernel		/boot/memtest86+.bin
quiet

title		Windows XP
root	(hd1,0)
map     (hd0) (hd1)
map     (hd1) (hd0)
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c60e7d99-8e0b-4a42-aff2-fb3127c43f0b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=06f85f2d-11dd-4161-8f32-3f6eb529ff8d none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location  of files loaded by Grub: ===================


   1.9GB: boot/grub/menu.lst
   1.9GB: boot/grub/stage2
   1.9GB: boot/initrd.img-2.6.27-7-generic
   2.0GB: boot/initrd.img-2.6.27-9-generic
   1.9GB: boot/vmlinuz-2.6.27-7-generic
   1.9GB: boot/vmlinuz-2.6.27-9-generic
   2.0GB: initrd.img
   1.9GB: initrd.img.old
   1.9GB: vmlinuz
   1.9GB: vmlinuz.old

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2009-01-27
It looks like the problem is your Windows install on sdb1 is missing its boot files, so probably the boot files were on the sda drive until you (unintentionally) deleted them when you installed Ubuntu to sda. Fortunately that type of problem is not usually hard to fix, so how about downloading the attached "WinXP_boot_files.zip" file to your Ubuntu desktop and do:
```
sudo mount /dev/sdb1 /mnt
cd ~/Desktop
unzip WinXP_boot_files.zip
sudo mv boot.ini ntldr NTDETECT.COM /mnt
```
Reboot, try XP from your Grub menu, and let me know how far you get. We can work from there if necessary.

---

### Post by oleksus on 2009-01-27
Thanks a million! It worked, and now I have dual booting option!


Your help is much appreciated, **caljohnsmith** and **theApokalypsis**!:KS

---

### Post by caljohnsmith on 2009-01-27
Great, glad to hear that was all it took to get XP booting again; cheers and have fun with XP and Ubuntu. :)

---

### Post by euchrid33 on 2009-01-27
For the record, I was able to get mine booting just fine using an even simpler addition to the GRUB file:

title Windows XP
root (hd0,1)
makeactive
chainloader +1 

I'm not sure what the extra commands recommended above would add, but I'm happy with it as is.

---

### Post by theApokalypsis on 2009-01-27
your welcome oleksus.

Definitly props though to caljohnsmith with the pwnage of forum support :)

---

