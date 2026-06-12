---
title: "GRUB Giving &quot;Error 18&quot;"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by Dark_Fire on 2009-01-26
Well I just installed Ubuntu 8.10, and it worked fine and all, but then when the grub loaded it gave me a "Error 18".

I sorta bypassed it by booting the live CD. I thought I can fix it but wasn't sure what to do. So when I restarted without CD it worked again. After restarting again it failed to work.

Im not sure if this means anything.

Thanks in advance,

Dark_Fire

---

### Post by caljohnsmith on 2009-01-26
Getting an inconsistent Grub error 18 is not a good sign. How about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu Live CD desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by Dark_Fire on 2009-01-26
can I run the script while using the installed Ubuntu or do I need to run it from a live CD?

---

### Post by caljohnsmith on 2009-01-26
If you can still boot into your Ubuntu install, then sure, you can run the script from there. :)

---

### Post by Dark_Fire on 2009-01-26
Thanks so much for your time :)

Like I said, after booting live CD I can boot back into it. I also restarted my machine a few times and it kept working. Im to scared to switch it off thou coz I have a feeling that a perm shutdown might result in another error...

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

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
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders, total 156368016 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d2cac

Partition  Boot        Start          End         Size  Id System

/dev/sda1    *            63  150,368,399  150,368,337  83 Linux
/dev/sda2        150,368,400  156,360,644    5,992,245   5 Extended
/dev/sda5        150,368,463  156,360,644    5,992,182  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
16 heads, 63 sectors/track, 775221 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa465e63f

Partition  Boot        Start          End         Size  Id System

/dev/sdb1                 63  781,419,743  781,419,681   7 HPFS/NTFS

/dev/sdb1 ends after the last cylinder of /dev/sdb

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="8b345d7f-f39a-44e0-99ee-dfcf7a5cd00d" TYPE="ext3" 
/dev/sda5: UUID="471f4215-6ce1-4f41-8d12-4868dd2a6f92" TYPE="swap" 
/dev/sdb1: UUID="F28435BE843585DF" LABEL="400" TYPE="ntfs" 

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
gvfs-fuse-daemon on /home/bernhard/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bernhard)
/dev/sdb1 on /media/400 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

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
# kopt=root=UUID=8b345d7f-f39a-44e0-99ee-dfcf7a5cd00d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8b345d7f-f39a-44e0-99ee-dfcf7a5cd00d

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
uuid		8b345d7f-f39a-44e0-99ee-dfcf7a5cd00d
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=8b345d7f-f39a-44e0-99ee-dfcf7a5cd00d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		8b345d7f-f39a-44e0-99ee-dfcf7a5cd00d
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=8b345d7f-f39a-44e0-99ee-dfcf7a5cd00d ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		8b345d7f-f39a-44e0-99ee-dfcf7a5cd00d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8b345d7f-f39a-44e0-99ee-dfcf7a5cd00d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		8b345d7f-f39a-44e0-99ee-dfcf7a5cd00d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8b345d7f-f39a-44e0-99ee-dfcf7a5cd00d ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		8b345d7f-f39a-44e0-99ee-dfcf7a5cd00d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8b345d7f-f39a-44e0-99ee-dfcf7a5cd00d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=471f4215-6ce1-4f41-8d12-4868dd2a6f92 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location  of files loaded by Grub: ===================


  68.6GB: boot/grub/menu.lst
  68.5GB: boot/grub/stage2
  68.6GB: boot/initrd.img-2.6.27-7-generic
  68.6GB: boot/initrd.img-2.6.27-9-generic
  68.6GB: boot/vmlinuz-2.6.27-7-generic
  68.7GB: boot/vmlinuz-2.6.27-9-generic
  68.6GB: initrd.img
  68.6GB: initrd.img.old
  68.7GB: vmlinuz
  68.6GB: vmlinuz.old

=============================== StdErr Messages: ===============================

No errors were reported.
```

Thanks again

---

### Post by caljohnsmith on 2009-01-26
You might be interested to know that a Grub error 18 is:
[QUOTE=Grub Manual]**Error 18**: Selected cylinder exceeds maximum supported by BIOS
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. [/QUOTE]
So usually you would get a Grub error 18 if you have an older BIOS that can't access anything on your HDD past either 8.4 GB or 137 GB (depending on its limitation), but it should be consistent; you shouldn't sometimes get the error and sometimes not, because the location of your Ubuntu boot files hasn't changed. The usual solution for a Grub error 18 is to create a small ~200 MB ext3 partition at the beginning of your drive, and then when you install Ubuntu, set the mount point on that partition as "/boot". That way all of Ubuntu's boot files are within the first 200 MB of the HDD, thus circumventing a Grub error 18. You could try that if you want, but I'm not sure it will help since your Grub error 18 is not consistent. Can you go into your BIOS and let me know what HDD related settings you have available? Look for things like "auto-detect", LBA, CHS, RAID, AHCI/HCI/EHCI vs. IDE, IDE-emulation, ACPI, DMA, etc. It might be that tweaking your BIOS settings for the HDD will prevent your Grub error 18. Let me know how that goes.

---

### Post by ddeo on 2009-02-04
Hi, I just installed ubuntu 8.04 on a 250MB HDD and I am getting error 18.  I will try to reinstall like you said.  Give a partition 200MB for /boot.  My question is what should the other partition look like?  Should it point to / ?  Should it be primary or logical?

Could you please give me a what a complete partitioning scheme would look like to fix the error 18 problem?

Much appreciated.  Ddeo

---

### Post by caljohnsmith on 2009-02-04
> **ddeo said:**
> Hi, I just installed ubuntu 8.04 on a 250MB HDD and I am getting error 18.  I will try to reinstall like you said.  Give a partition 200MB for /boot.  My question is what should the other partition look like?  Should it point to / ?  Should it be primary or logical?

Could you please give me a what a complete partitioning scheme would look like to fix the error 18 problem?

Much appreciated.  Ddeo
When you say the "other partition", do you mean the main Ubuntu partition? If so, the mount point of Ubuntu's main partition should be "/", and the partition can be either primary or logical, it doesn't matter. A complete partition scheme might look simply like:
```
sda1  200 MB "/boot"
sda2  extended partition
  sda5  Ubuntu main partition "/"
  sda6  Home partition for your personal files "/home"
  sda7  swap partition
```
I included the extra "/home" partition above, but you don't have to do that if you don't want; it's generally recommended to do that so you can keep your personal files separate from the main Ubuntu partition. But the main thing is to make sure the /boot partition is at the beginning of the drive, and other than that, you're basically free to do as you wish. Good luck and let me know how it goes.

---

### Post by ddeo on 2009-02-04
Hi, thank you for your response.  How do I make an extended partition?  I created the sda1 for /boot

Should the extended be primary or logical?  Anyway there is no choice for extended.  But this is probably because I am a noob

---

### Post by caljohnsmith on 2009-02-04
How are you making your partitions? I think I would recommend setting up your partitions before running the installer; you can do that by opening the partition editor "gparted" under (System > Admin > Partition Editor). Gparted will allow you to set up all your partitions, and then when you go through the Ubuntu installer, choose the "manual" option for partitioning so you can select the partitions you created. Keep in mind that the "extended partition" is the container for all your logical partitions. That means you would create the extended partition first while you are in gparted, and then create all the logical partitions you want inside of it. Let me know how that goes.

---

### Post by ddeo on 2009-02-04
I am creating the partitions with in the ubuntu installer using the manual option like you said.  There is no way to create an extended partition as far as I can see.  I have created the first partition for /boot

Now I select free space and select create partition.  There is no extended option....  Please advise

Also, I do want to put the /home on its own partition because I am mostly using box as a server for FTP.   So I would like to assign roughly 2 gigs to /home

---

### Post by caljohnsmith on 2009-02-04
That's fine if you want to use the "manual" partition option to set up all your partitions; if you use that, just make your logical partitions as you wish and I believe the installer creates the extended partition for you.

---

### Post by ddeo on 2009-02-04
What would you recommend I set for partition size for /?  and how much for swap?  I have 1.5gig ram

---

### Post by caljohnsmith on 2009-02-04
You could use 10 GB for Ubuntu's main partition "/", and a 3 GB swap partition should be ample. If you plan on installing lots and lots of software in Ubuntu, you might want to use maybe 15 GB for the main Ubuntu partition.

---

### Post by ddeo on 2009-02-04
Installing now......

<< fingers crossed >>

---

### Post by ddeo on 2009-02-04
You saved me!!!!

Thank you for your help.  :KS  Ddeo

---

### Post by caljohnsmith on 2009-02-04
Glad to hear that worked OK, ddeo; cheers and enjoy your new Ubuntu install. :)

---

