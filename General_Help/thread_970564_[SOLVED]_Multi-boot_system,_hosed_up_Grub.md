---
title: "[SOLVED] Multi-boot system, hosed up Grub"
date: 2008-11-04
forum: General Help
---

### Post by Matt_D on 2008-11-04
This is a long post, hopefully it's clear what I did and what I was trying to do.

 I had a dual-boot system with Windows XP and Ubuntu 8.04, installed on the same hard drive. I installed a new (old, new to this system) 80GB drive to try out openSuse 11. The DVD install went fine, though I did get confused when it came time to install GRUB, and also when creating a /boot partition. I already have a /boot on my Win/Ubu disk, but I selected not to mount that one when partitioning for openSuse, and instead created another /boot partition in which I installed GRUB. So, when I rebooted I got a GRUB error 15. I then checked the boot order in my BIOS, and moved the openSuse disk up to 1st, and I can boot openSuse okay. Using SuperGrub I could boot into my Ubuntu install, but no Windows XP. I copied the entries from my Ubuntu menu.lst into my openSuse menu.lst:

[FONT="Courier New"][SIZE="2"]
title Ubuntu 8.04.1, kernel 2.6.24-21-generic
root (hd0,5)
kernel /vmlinuz-2.6.24-21-generic root=UUID=5b7dc39c-6414-4755-afea-630a7673a5d2 ro quiet splash
initrd /initrd.img-2.6.24-21-generic
quiet
FAT32 (LBA)[/SIZE][/FONT]

I then changed (hd0,5) to read (hd1,5) since I changed the order in BIOS. This works great for selecting between openSuse & Ubuntu when booting, but Windows still won't boot ( also changed hd0 to hd1 for Windows). If I make my Win/Ubu disk the first boot disk I get a GRUB error.

My question is, how do I get a working GRUB config which lists all 3 Operating Systems, and allows me to boot into them?

Here's my fisk -l output from openSuse:
[FONT="Courier New"][SIZE="2"]
Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xee800574

Device Boot Start End Blocks Id System
/dev/sda1 1 6527 52428096 7 HPFS/NTFS
/dev/sda2 * 6528 36483 240621570 f W95 Ext'd (LBA)
/dev/sda5 6528 26108 157284351 7 HPFS/NTFS
/dev/sda6 26109 26135 216846 83 Linux
/dev/sda7 26136 35059 71681998+ 83 Linux
/dev/sda8 35060 36334 10241406 83 Linux
/dev/sda9 36335 36483 1196811 82 Linux swap / Solaris

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000348a8

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 9961 80011701 f W95 Ext'd (LBA)
/dev/sdb5 1960 9961 64276065 83 Linux
/dev/sdb6 1 32 256945+ 83 Linux
/dev/sdb7 33 1959 15478596 83 Linux

Partition table entries are not in disk order

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x54eeaef8

Device Boot Start End Blocks Id System
/dev/sdc1 * 1 60801 488384001 7 HPFS/NTFS

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

Device Boot Start End Blocks Id System
/dev/sdd1 * 1 19457 156288321 c W95 FAT32 (LBA)
Reply With Quote
[/SIZE][/FONT]
My ultimate goal would be to get my old Ubuntu grub back, and add the opensuse choice to that list.  I'd also like to understand the how & why, so I can have the option to use my 2nd drive to try beta versions of upcoming releases without continually hosing my working GRUB.

---

### Post by caljohnsmith on 2008-11-04
> **Matt_D said:**
> 
My ultimate goal would be to get my old Ubuntu grub back, and add the opensuse choice to that list.  I'd also like to understand the how & why, so I can have the option to use my 2nd drive to try beta versions of upcoming releases without continually hosing my working GRUB.
OK, to first reinstall Grub to the MBR (Master Boot Record) of your sda drive and point it to your /boot Ubuntu partition, you can use:
```
sudo grub
grub> root (hd0,5)
grub> setup (hd0)
grub> quit
```
Then you should be able to boot your sda drive on start up, and get the Ubuntu Grub menu. Once you get that far, you can always add OpenSUSE's entries to your Ubuntu menu.lst, and change the "root" line to "root (hd1,5)", similar to what you did with Ubuntu in OpenSUSE's menu.lst. That will work if the OpenSUSE drive is second in the BIOS boot order, i.e. (hd1), after the Ubuntu drive (hd0). One disadvantage of copying OpenSUSE's entries over to Ubuntu is that you'll have to do that each time you get a kernel upgrade in OpenSUSE. You might want to consider simply linking to OpenSUSE's menu.lst in your Ubuntu menu.lst with:
```
title OpenSUSE Grub menu
configfile (hd1,5)/boot/grub/menu.lst
```
Then when OpenSUSE's menu.lst gets updated, you don't have to do anything. 

Anyway, give the above a shot and let me know how it goes. :)

---

### Post by Matt_D on 2008-11-04
Here's what I did:

booted into Ubuntu, opened terminal, 
```
sudo grub
grub> root (hd0,5)
grub> setup (hd0)
grub> quit
```

No errors.  Rebooted, entered BIOS setup, changed hard drive boot order to boot Ubuntu & WinXP disk first.  Got Grub Error 15.  Changed boot order to boot openSuse first, got the openSuse grub menu.  It seems that I need to boot the Ubuntu drive first to get that grub menu to show, but when I do that I get the error 15.

---

### Post by caljohnsmith on 2008-11-04
Do you get the Grub error 15 before seeing a Grub menu, or before seeing the text "Press ESC to see menu", or do you get the error after selecting an OS in the Grub menu? And do you have "hiddenmenu" commented in your Ubuntu menu.lst:
```
# hiddenmenu
```
Also, please go ahead and post your full Ubuntu menu.lst and the other information from:
```
sudo blkid
ls -lR /boot
cat /boot/grub/menu.lst
```
And lastly, just to make sure Grub is installed correctly to sda, please post the following:
```
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump
```

---

### Post by Matt_D on 2008-11-04
I get the error 15 when GRUB tries to start.  I don't get to see the menu.  Right now I'm burning a live CD, going to boot into that, go to terminal, and try the grub commands.  

Here's the output you asked for:
sudo blkid
```
matt@matt-ubuntubox2:~$ sudo blkid
[sudo] password for matt: 
/dev/sda5: UUID="186b6811-89c5-4c0d-b8b0-f8d3f022416d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="125069C95069B45F" TYPE="ntfs" 
/dev/sdb5: UUID="825CB1845CB1740F" LABEL="Apps" TYPE="ntfs" 
/dev/sdb6: UUID="c3cf901e-177a-48aa-a6d5-ac24602235a8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb7: UUID="e19682e0-2f66-487c-8ddc-a8baf8995ed1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb8: UUID="5b7dc39c-6414-4755-afea-630a7673a5d2" TYPE="ext3" 
/dev/sdb9: TYPE="swap" LABEL="SWAP-sda9" UUID="25eba00d-2707-4cfe-9ff6-c80f457b5308" 
/dev/sdc1: LABEL="My Book" UUID="3717-D230" TYPE="vfat" 
/dev/sdd1: UUID="55D123D9E79ABF54" LABEL="OneTouch4 Plus" TYPE="ntfs" 
/dev/sda6: UUID="01c2285a-730f-4e9f-ba4a-b5f36b985dfd" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="7eff3d18-a5b0-418c-9841-8f4f33d80902" SEC_TYPE="ext2" TYPE="ext3" 

```

ls -lR /boot
```
matt@matt-ubuntubox2:~$ ls -lR /boot
/boot:
total 36082
-rw-r--r-- 1 root root  422667 2008-08-20 23:46 abi-2.6.24-19-generic
-rw-r--r-- 1 root root  422838 2008-10-21 22:12 abi-2.6.24-21-generic
-rw-r--r-- 1 root root   80049 2008-08-20 23:46 config-2.6.24-19-generic
-rw-r--r-- 1 root root   80062 2008-10-21 22:12 config-2.6.24-21-generic
drwxr-xr-x 2 root root    1024 2008-11-01 17:49 grub
-rw-r--r-- 1 root root 7501566 2008-10-31 19:32 initrd.img-2.6.24-19-generic
-rw-r--r-- 1 root root 7500272 2008-08-12 10:59 initrd.img-2.6.24-19-generic.bak
-rw-r--r-- 1 root root 7501904 2008-10-31 19:32 initrd.img-2.6.24-21-generic
-rw-r--r-- 1 root root 7502678 2008-10-31 19:32 initrd.img-2.6.24-21-generic.bak
drwx------ 2 root root   12288 2008-05-21 02:37 lost+found
-rw-r--r-- 1 root root  103204 2007-09-28 05:06 memtest86+.bin
-rw-r--r-- 1 root root  905170 2008-08-20 23:46 System.map-2.6.24-19-generic
-rw-r--r-- 1 root root  905617 2008-10-21 22:12 System.map-2.6.24-21-generic
-rw-r--r-- 1 root root 1921464 2008-08-20 23:46 vmlinuz-2.6.24-19-generic
-rw-r--r-- 1 root root 1920760 2008-10-21 22:12 vmlinuz-2.6.24-21-generic

/boot/grub:
total 174
-rw-r--r-- 1 root root    197 2008-05-20 21:49 default
-rw-r--r-- 1 root root     30 2008-05-20 21:49 device.map
-rw-r--r-- 1 root root   8056 2008-05-20 21:49 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-05-20 21:49 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-05-20 21:49 installed-version
-rw-r--r-- 1 root root   8608 2008-05-20 21:49 jfs_stage1_5
-rw-r--r-- 1 root root   4969 2008-11-01 17:49 menu.lst
-rw-r--r-- 1 root root   4969 2008-11-01 17:49 menu.lst~
-rw-r--r-- 1 root root   7324 2008-05-20 21:49 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-05-20 21:49 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-05-20 21:49 stage1
-rw-r--r-- 1 root root 108356 2008-05-20 21:49 stage2
-rw-r--r-- 1 root root   9276 2008-05-20 21:49 xfs_stage1_5
ls: cannot open directory /boot/lost+found: Permission denied


```

ls -lR /boot
```
matt@matt-ubuntubox2:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=5b7dc39c-6414-4755-afea-630a7673a5d2 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,5)
kernel		/vmlinuz-2.6.24-21-generic root=UUID=5b7dc39c-6414-4755-afea-630a7673a5d2 ro quiet splash
initrd		/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,5)
kernel		/vmlinuz-2.6.24-21-generic root=UUID=5b7dc39c-6414-4755-afea-630a7673a5d2 ro single
initrd		/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,5)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=5b7dc39c-6414-4755-afea-630a7673a5d2 ro quiet splash
initrd		/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,5)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=5b7dc39c-6414-4755-afea-630a7673a5d2 ro single
initrd		/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,5)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

matt@matt-ubuntubox2:~$ 



```

---

### Post by Matt_D on 2008-11-04
> **caljohnsmith said:**
> OK, to first reinstall Grub to the MBR (Master Boot Record) of your sda drive and point it to your /boot Ubuntu partition, you can use:
```
sudo grub
grub> root (hd0,5)
grub> setup (hd0)
grub> quit
```
Then you should be able to boot your sda drive on start up, and get the Ubuntu Grub menu. Once you get that far, you can always add OpenSUSE's entries to your Ubuntu menu.lst, and change the "root" line to "root (hd1,5)", similar to what you did with Ubuntu in OpenSUSE's menu.lst. That will work if the OpenSUSE drive is second in the BIOS boot order, i.e. (hd1), after the Ubuntu drive (hd0). One disadvantage of copying OpenSUSE's entries over to Ubuntu is that you'll have to do that each time you get a kernel upgrade in OpenSUSE. You might want to consider simply linking to OpenSUSE's menu.lst in your Ubuntu menu.lst with:
```
title OpenSUSE Grub menu
configfile (hd1,5)/boot/grub/menu.lst
```
Then when OpenSUSE's menu.lst gets updated, you don't have to do anything. 

Anyway, give the above a shot and let me know how it goes. :)

Okay, got it to work using your instructions, with 1 modification.  I had to boot a live cd, and use that terminal.  I read somewhere that you can't re-install grub in you're using that hard drive, or something to that effect.  My only issue now is when I select the OpenSUSE Grub menu, then choose OpenSuse from that menu I get a file not found error.  I think it's because the menu.lst point to hd0 and not hd1.  Going to switch that and see what happens.  Will OpenSUSE, or any other distro on that drive in the future use hd1 when updating it's menu.lst?  Just curious where that comes from.  Thanks so much for the quick and useful replies.

Edit:
booted into OpenSuse (put the opensuse drive first in BIOS again, temporarily).  Edited menu.lst, changing all hd0 references to hd1 (except 1, left 1 just in case).  Rebooted, changed boot order back to permanent setup of Ubuntu disk 1st, openSuse disk 2nd.  Now I get my Ubuntu grub, where I can choose to boot Ubuntu, Windows XP, or to look at the OpenSuse Grub menu, where I can boot into OpenSuse.  All load when selected, thanks again for helping me out.

---

### Post by caljohnsmith on 2008-11-04
> **Matt_D said:**
> Okay, got it to work using your instructions, with 1 modification.  I had to boot a live cd, and use that terminal.  I read somewhere that you can't re-install grub in you're using that hard drive, or something to that effect.  My only issue now is when I select the OpenSUSE Grub menu, then choose OpenSuse from that menu I get a file not found error.  I think it's because the menu.lst point to hd0 and not hd1.  Going to switch that and see what happens.  Will OpenSUSE, or any other distro on that drive in the future use hd1 when updating it's menu.lst?  Just curious where that comes from.  Thanks so much for the quick and useful replies.
So you are booting from sda now? And yes, I forgot to mention that the OpenSUSE Grub entries would need to be modified, because if you boot from the sda drive, then sda is (hd0) on start up, and if the OpenSUSE drive is second in the boot order, it is (hd1). But instead of using "configfile" to link directly to the OpenSUSE menu.lst, a better solution would be to put the following in Ubuntu's menu.lst:
```
title OpenSUSE Grub menu
rootnoverify (hd1)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
What that does is boot the OpenSUSE drive (hd1), but it uses Grub's mapping technique into fooling the OpenSUSE drive that it is (hd0) instead of (hd1) in the boot order. That way you shouldn't have to modify OpenSUSE's menu.lst. The other advantage is that if something happens to the Ubuntu drive where you can't boot it, you can boot your OpenSUSE drive on start up and not have to change the Grub menu entries to use (hd0) instead of (hd1). Does that make sense or did I just make it more convoluted? :)

---

### Post by Matt_D on 2008-11-04
what you're saying makes perfect sense, however, something isn't working quite right.  When I select OpenSUSE Grub menu from my ubuntu menu.lst, it loads grub, but it loads the ubuntu grub menu again.  Sort of an endless loop (if I'm stupid enough to keep hitting openSuse Grub menu).  Going to try reversing the map entries you listed and see what happens.

edit:  tried 
map (hd1) (hd0)
map (hd0) (hd1)

didn't work.  
Very close to getting this perfect, but hitting a snag with the chainloader.

---

### Post by caljohnsmith on 2008-11-04
It sounds like the Grub in the MBR of your OpenSUSE drive is pointing to the Ubuntu drive. How about posting the following commands so we can know for sure:
```
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump
sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump
```

---

### Post by Matt_D on 2008-11-04
this is from the ubuntu terminal, going to boot into openSuse and try the same thing.  
```


matt@matt-ubuntubox2:~$ sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB 
matt@matt-ubuntubox2:~$ sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB 
matt@matt-ubuntubox2:~$ sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump
0000000 ff05                                   
0000002
matt@matt-ubuntubox2:~$ sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump
0000000 ff05                                   
0000002
matt@matt-ubuntubox2:~$ 

```

---

### Post by caljohnsmith on 2008-11-04
OK, according to those commands you have Grub installed to the MBR of both sda and sdb, and the Grub in both drives correctly points to the 6th partition on the same drive for its boot files. So when you boot the OpenSUSE drive, whether you do it through Ubuntu's menu.lst or directly on start up, you should be getting the OpenSUSE menu.lst. Are the two menu.lst files (Ubuntu and OpenSUSE) similar enough that you might be thinking they are the same? You could always change something superficial in the "title" of an entry to make it clear which menu.lst it is.

---

### Post by Matt_D on 2008-11-04
no, there's not mistaking which menu is loading.  OpenSUSE's grub menu has a green background, and I've edited the menu.lst to only show OpenSUSE options.  The Ubuntu grub menu has all the choices.  Is there some variation of the grub commands I ran earlier to recreate the ubuntu grub that I could run to recreate the proper openSuse ones?  If I boot into a live cd and run this:
```

sudo grub
grub> root (hd1,5)
grub> setup (hd1)
grub> quit

```
would I then be re-installing grub on hd1?

---

### Post by Matt_D on 2008-11-04
Here's my OpenSUSE menu.lst if that helps any:

```

# Modified by YaST2. Last modification on Mon Nov  3 17:10:46 CST 2008
default 0
timeout 8
gfxmenu (hd0,5)/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 11.0 - 2.6.25.18-0.2 (pae)
    root (hd0,5)
    kernel /vmlinuz-2.6.25.18-0.2-pae root=/dev/disk/by-id/scsi-SATA_Maxtor_6L080L0_L21N8QYG-part7 resume=/dev/sda9 splash=silent showopts vga=0x31a
    initrd /initrd-2.6.25.18-0.2-pae

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.0 - 2.6.25.18-0.2 (pae)
    root (hd0,5)
    kernel /vmlinuz-2.6.25.18-0.2-pae root=/dev/disk/by-id/scsi-SATA_Maxtor_6L080L0_L21N8QYG-part7 showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off x11failsafe vga=0x31a
    initrd /initrd-2.6.25.18-0.2-pae

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 11.0 - 2.6.25.18-0.2 (default)
    root (hd0,5)
    kernel /vmlinuz-2.6.25.18-0.2-default root=/dev/disk/by-id/scsi-SATA_Maxtor_6L080L0_L21N8QYG-part7 resume=/dev/sda9 splash=silent showopts vga=0x31a
    initrd /initrd-2.6.25.18-0.2-default

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.0 - 2.6.25.18-0.2 (default)
    root (hd0,5)
    kernel /vmlinuz-2.6.25.18-0.2-default root=/dev/disk/by-id/scsi-SATA_Maxtor_6L080L0_L21N8QYG-part7 showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off x11failsafe vga=0x31a
    initrd /initrd-2.6.25.18-0.2-default



```

---

### Post by caljohnsmith on 2008-11-04
Yes, you can use the commands exactly as you have them written to reinstall Grub to the MBR of sdb and point it to sdb6 for its boot files. But according to the dd commands you ran, Grub is all ready installed correctly to the sdb drive. In Ubuntu's menu.lst, are you sure you have:
```
title OpenSUSE Grub menu
rootnoverify [COLOR="Red"](hd1)[/COLOR]
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
You're using (hd1) and not (hd0), right? If you have it right, I'm not sure off hand what would be causing Grub to link back to the Ubuntu menu.lst. How about trying:
```
title OpenSUSE Grub menu
root [COLOR="Red"](hd1,5)[/COLOR]
map        (hd0) (hd1)
map        (hd1) (hd0)
configfile /boot/grub/menu.lst
```
I believe the above entry should accomplish the same end result. Give that a shot and let me know what happens.

---

### Post by Matt_D on 2008-11-04
```

title OpenSUSE Grub menu
root (hd1,5)
map        (hd0) (hd1)
map        (hd1) (hd0)
configfile /boot/grub/menu.lst

```

Using the above, when I select OpenSUSE Grub menu from the Ubuntu menu.lst, it sort of loads the OpenSUSE Grub menu, meaning it has the right choices, but does not look like the normal one, it looks like the ubuntu menu with suse choices.  Regardless, it does not load any of the choices in that menu, gives an error 15, file not found message.

---

### Post by caljohnsmith on 2008-11-04
When you get the Grub error 15 from the SUSE entries, are the SUSE entries using (hd0) or (hd1)? I would think they are using (hd1) to get the error 15 while using the mapping technique, because with the remapping, the SUSE entries should use (hd0) to correctly boot; and the Ubuntu entries should use (hd1). But what really is strange is getting the Ubuntu Grub menu when booting the SUSE drive with that first entry I gave, even though the SUSE drive appears to have Grub correctly configured in its MBR. How about if you remove the mapping from Ubuntu's menu.lst for OpenSUSE:
```
title OpenSUSE Grub menu
rootnoverify (hd1)
chainloader +1
```
Does that then at least get you the OpenSUSE menu when you select it on start up?

---

### Post by Matt_D on 2008-11-04
that gives a whole new level of error(s):p

Error 18: Selected cylinder exceeds maximu suported by BIOS

That's a  good one I think:-s

---

