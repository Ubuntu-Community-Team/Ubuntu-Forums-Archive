---
title: "Grub Error 23: Error while parsing number"
date: 2009-02-22
forum: Installation &amp; Upgrades
---

### Post by mikedmor on 2009-02-22
Hey,
i just recently installed Ubuntu 8.10 to my Desktop; I originally had Vista & Windows 7 but now i cant access neither of them because of this Error i keep getting. I CAN access Ubuntu this error only happens when i try to boot Windows.

I was wondering if i could setup GRUB to boot to Windows Boot manager so i could select which windows OS to boot from. Im still in the process of converting over but i still need my other partition.

This is all being done from 3 different Hard drives so i know i didnt over right them (also i know by fdisk -l). I will post the Grub Boot here and the out put of fdisk -l so you can see if you know whats going on here.

---

### Post by mikedmor on 2009-02-22
sudo fdisk -l

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x086cb148

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121602   976759808    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006dad3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9324    74894998+  83  Linux
/dev/sdb2            9325        9726     3229065    5  Extended
/dev/sdb5            9325        9726     3229033+  82  Linux swap / Solaris

Disk /dev/sdc: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95b5d416

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30394   244136960    7  HPFS/NTFS
```


/boot/grub/menu.lst


```
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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		a14c41d1-ab65-48ec-86ae-615d8a50fd59
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=a14c41d1-ab65-48ec-86ae-615d8a50fd59 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		a14c41d1-ab65-48ec-86ae-615d8a50fd59
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=a14c41d1-ab65-48ec-86ae-615d8a50fd59 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, memtest86+
uuid		a14c41d1-ab65-48ec-86ae-615d8a50fd59
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Boot Manager
root		(sda1,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by caljohnsmith on 2009-02-22
> **mikedmor said:**
> ```

title		Windows Boot Manager
root		[COLOR="Blue"](sda1,0)[/COLOR]
savedefault
makeactive
chainloader	+1

```
All HDDs are (hdX,Y) to Grub, regardless of whether the drive is IDE or SATA. Since I don't know which drive you are booting on start up, there are three possible entries for booting Windows:
```
title       Windows (hd0)
root       (hd0,0)
chainloader +1

title       Windows (hd1)
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title       Windows (hd2)
rootnoverify     (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
How about putting all three in your menu.lst, try each one, and let me know what happens. Also, if you want to modify your Windows boot manager to boot both Vista and Win 7, a really good program that will help you do that is "[EasyBCD]("http://neosmart.net/dl.php?id=1")." Let me know how that goes or if you run into problems.

---

### Post by mikedmor on 2009-02-22
That did the trick! Second option worked like a charm.

and i know about EasyBCD i use it for my windows partition. but isnt it only for windows?

One more question that you might be able to answer about my boot, for some reason most the time my ubuntu first option will NOT boot. the only way to fix this is to unplug my other two hard drives and  reboot then plug them back in. but after that i can boot about 5 to 10 times without a problem. it usually gets stuck on boot at about 2 1/2 bars.

---

### Post by caljohnsmith on 2009-02-22
> **mikedmor said:**
> 
and i know about EasyBCD i use it for my windows partition. but isnt it only for windows?

Yes, EasyBCD is only for Windows, but I thought that's what you wanted when you said:
> **mikedmor]I was wondering if i could setup GRUB to boot to Windows Boot manager so i could select which windows OS to boot from. Im still in the process of converting over but i still need my other partition.
[/QUOTE]
So I guess I misunderstood said:**
> 
One more question that you might be able to answer about my boot, for some reason most the time my ubuntu first option will NOT boot. the only way to fix this is to unplug my other two hard drives and  reboot then plug them back in. but after that i can boot about 5 to 10 times without a problem. it usually gets stuck on boot at about 2 1/2 bars.
I have no idea since I don't have much info about your setup at this point; in order to get a clearer picture of your setup, how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post. The results of that script will help clarify your setup.

---

### Post by mikedmor on 2009-02-22
Sorry, No worries about the Vista and Windows 7. I originally had been booting both those before. All i needed was to get grub to boot from my windows vista hard drive then that put me in Windows Boot Manager where i could select either Windows Vista or Windows 7. So all that worked out just how i wanted it too.

Here is the RESULTS.txt it gave me:


```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

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
    Boot files/dirs:   /Windows/System32/winload.exe

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /ubuntu/winboot/menu.lst /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /grldr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0006dad3

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   149,790,059   149,789,997  83 Linux
/dev/sda2         149,790,060   156,248,189     6,458,130   5 Extended
/dev/sda5         149,790,123   156,248,189     6,458,067  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x95b5d416

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   488,275,967   488,273,920   7 HPFS/NTFS


Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x086cb148

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS

/dev/sdc1 ends after the last cylinder of /dev/sdc

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="a14c41d1-ab65-48ec-86ae-615d8a50fd59" TYPE="ext3" 
/dev/sda5: UUID="feaa44e2-68d5-43c0-aff9-e406fd23a661" TYPE="swap" 
/dev/sdb1: UUID="0A1076A210769483" LABEL="Windows 7" TYPE="ntfs" 
/dev/sdc1: UUID="18D8ECDBD8ECB7E0" LABEL="Vista" TYPE="ntfs" 

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
gvfs-fuse-daemon on /home/michael/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=michael)


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
# kopt=root=UUID=a14c41d1-ab65-48ec-86ae-615d8a50fd59 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a14c41d1-ab65-48ec-86ae-615d8a50fd59

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		a14c41d1-ab65-48ec-86ae-615d8a50fd59
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=a14c41d1-ab65-48ec-86ae-615d8a50fd59 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		a14c41d1-ab65-48ec-86ae-615d8a50fd59
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=a14c41d1-ab65-48ec-86ae-615d8a50fd59 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, memtest86+
uuid		a14c41d1-ab65-48ec-86ae-615d8a50fd59
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1

title       Windows Boot Manager
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=a14c41d1-ab65-48ec-86ae-615d8a50fd59 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc5
UUID=feaa44e2-68d5-43c0-aff9-e406fd23a661 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   7.2GB: boot/grub/menu.lst
   7.3GB: boot/grub/stage2
   7.2GB: boot/initrd.img-2.6.27-11-generic
   7.2GB: boot/initrd.img-2.6.27-7-generic
   7.3GB: boot/vmlinuz-2.6.27-11-generic
   7.3GB: boot/vmlinuz-2.6.27-7-generic
   7.2GB: initrd.img
   7.2GB: initrd.img.old
   7.3GB: vmlinuz
   7.3GB: vmlinuz.old

======================== sdc1/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	fallback 3
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 4
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 5
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt
```

---

### Post by caljohnsmith on 2009-02-22
Based on the results of the script, there's nothing obvious that I can see about your setup that would cause it to hang at boot up some of the time, but it would take a much more detailed analysis of your setup I think to figure that out. My only suggestion would be to remove the "quiet splash" options at the end of the kernel line for the Ubuntu entry, that way you can watch the boot messages and see exactly where Ubuntu hangs sometimes:
```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		a14c41d1-ab65-48ec-86ae-615d8a50fd59
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=a14c41d1-ab65-48ec-86ae-615d8a50fd59 ro [COLOR="Red"]quiet splash [/COLOR]
initrd		/boot/initrd.img-2.6.27-11-generic
quiet
```
Let me know how that goes.

---

### Post by mikedmor on 2009-02-22
ok i removed the quite splash. It might take some time. but i will post back as soon as it stops letting you know just where exactly the problem is occurring.

Thanks for the help.

---

### Post by mikedmor on 2009-02-22
Well i got it to freeze again, not sure if thats a good thing. It seems to just stop at

usbcore: registered new interface driver ndiswrapper

i think i may know how to fix this... but i would rather get an answer from you guys before messing with it myself

Edit: I just restarted and it froze some where different. here is where it stopped

Linux agpgart interface v0.103

---

### Post by caljohnsmith on 2009-02-22
I suppose you're probably all ready aware that ndiswrapper is for using your Windows drivers with your wireless card, but it seems strange if that's what makes your computer hang only sometimes, but not consistently. I suppose you could try reinstalling ndiswrapper and see if that makes any difference. Other than that, I'm not sure since the problem is erratic; if it happened consistently it would be easier to troubleshoot I think.

EDIT: Maybe just as a sanity check it would be good to run some HDD diagnostic tests on that HDD just to make sure that's not the issue.

---

### Post by mikedmor on 2009-02-22
well i decided to ultimately just remove vista and windows 7. it turns out that ever since i installed ubuntu they freeze as soon as the login screen loads. unless i start them in safe mode. im going to back up all my information so i can use it on linux...

Thanks for all the help.


Also i found out why i was having that problem. it only occurs when i plug my hard drives in a different order. i must have plugged them in differently when i was messing with the grub boot to try to get it working.

---

