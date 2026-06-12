---
title: "GRUB Error 21: Selected Disk Does Not Exist..."
date: 2009-02-06
forum: Installation &amp; Upgrades
---

### Post by casparov on 2009-02-06
Hi, Everyone... 

I have received excellent help from Tommcd on an attempt to migrate Ubuntu, existing by itself on an IDE disk,to a multiboot arrangement on a new SATA disk.  That process can be viewed here: [http://ubuntuforums.org/showthread.php?p=6635866#post6635866](http://ubuntuforums.org/showthread.php?p=6635866#post6635866) 

I realize that this post constitutes a cross-post in part, but the current error results from attempting to reinstall GRUB, what I thought would be the simplest step. 

After reinstalling GRUB (I used the "sudo grub; find /boot/grub/stage1; root (hd0,5); setup (hd0)" routine) I rebooted after the process appeared to proceed w/o error.

Upon finding the GRUB boot list I selected 8.04 Ubuntu and was greeted by the intractable (for me) "error 21: selected disk does not exist".

I found on other forum replies that a problem seems to exist when migrating to SATA disks, or something. Anyway, I then tried installing 8.10 from the Live CD and nearly made perilous changes to the size of my main Windows partition. I quit the install but impaired the size of my first partition, an unused W98 area.

Is there any way to fix the Ubuntu boot error 21? I am not really literate in Linux command line syntax, so any very complicated fix will not be good for me.

It may be that I should just wipe out my copied and pasted 8.04 partition and start over w/ 8.10. (I noticed that the installation for 8.10 asked whether it should import user settings from my "sda6" disk, which is the copied Ubuntu 8/04. Perhaps this gives me the best of both worlds.)

Just a bit flummoxed here...

C.

---

### Post by Pumalite on 2009-02-06
[http://users.bigpond.net.au/hermanzone/p15.htm#21](http://users.bigpond.net.au/hermanzone/p15.htm#21)

---

### Post by caljohnsmith on 2009-02-06
In order to get a clearer picture of your setup, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to the Live CD desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by casparov on 2009-02-06
Pumalite and CalJohn...

Thanks so much for your replies--I truly appreciate them. 

CalJohn...  I will do as you indicate but have a couple of prior commitments just now.  I will reply w/ the information shortly.

Thanks again,

Casp

---

### Post by casparov on 2009-02-06
CalJohn... 

I've spent a good deal of time attempting to access the MBR information that the boot info script should give us.  However, all I can get is this: 

ubuntu@ubuntu:~$ sudo bash ~/desktop/boot_info_script*.sh
bash: /home/ubuntu/desktop/boot_info_script*.sh: No such file or directory
ubuntu@ubuntu:~$ sudo bash ~/desktop/boot_info_script024.sh
bash: /home/ubuntu/desktop/boot_info_script024.sh: No such file or directory
ubuntu@ubuntu:~$ sudo bash
root@ubuntu:~# ~/desktop/boot_info_script024.sh
bash: /home/ubuntu/desktop/boot_info_script024.sh: No such file or directory
root@ubuntu:~# 


I cannot get the script to run and got pretty frustrated trying.  (I tried many more permutations than those, above, just for fun.)  Though the file downloaded just fine--and I am sending you this from the Live CD boot--I just can't seem to get things to run.

Do you have any other suggestions? 

Thanks so much,

C.

---

### Post by caljohnsmith on 2009-02-06
From those errors you posted, it's not that the script isn't working, it's that the script doesn't exist on your desktop. Did you download the script to your desktop? Did you check to see that it is on your desktop? You can also check in the terminal by doing:
```
ls -l ~/Desktop
```
And you should see the boot_info_script024.sh listed there. How about trying again and let me know how it goes, or if you still run into problems.

---

### Post by meierfra. on 2009-02-06
> sudo bash ~/[COLOR="Red"]d[/COLOR]esktop/boot_info_script*.sh

Typo: Desktop needs a capital "D"

---

### Post by casparov on 2009-02-06
CalJohn... 

Thanks for every second of your efforts...  

Yes, the script was sitting on the desktop, and I double-clicked it to see what it said.  (That is how I knew the current version was script024.)  I also used its suggested line command and got the same result. 

I will try your latest in a bit,

Casp

---

### Post by casparov on 2009-02-08
CalJohn...  

Thank-you for all the help--apologies for being so slow about the latest.  

You (and the other sleuth) were right--I didn't capitalize the "d"...  

Okay, here is the copied text (sorry for the length):  

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTLDR /NTDETECT.COM /ntdetect.com 
                       /wubildr.mbr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/menu.lst /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4405834f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    52,146,989    52,146,927   c W95 FAT32 (LBA)
/dev/sda2         293,587,875   976,768,064   683,180,190   5 Extended
/dev/sda5         293,587,938   704,867,939   411,280,002   7 HPFS/NTFS
/dev/sda6         704,868,003   976,768,064   271,900,062  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="8128-9B56" TYPE="vfat" 
/dev/sda5: UUID="96848431848415C1" TYPE="ntfs" 
/dev/sda6: UUID="165f6e79-73ad-41eb-914f-937a74fdd777" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(2)\WINNT

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINNT="Microsoft Windows 2000 Professional" /fastdetect

C:\="Microsoft Windows" 

c:\wubildr.mbr="Ubuntu"


======================== sda5/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 3
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt

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
# kopt=root=UUID=165f6e79-73ad-41eb-914f-937a74fdd777 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=165f6e79-73ad-41eb-914f-937a74fdd777 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=165f6e79-73ad-41eb-914f-937a74fdd777 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=165f6e79-73ad-41eb-914f-937a74fdd777 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=165f6e79-73ad-41eb-914f-937a74fdd777 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=165f6e79-73ad-41eb-914f-937a74fdd777 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=165f6e79-73ad-41eb-914f-937a74fdd777 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=165f6e79-73ad-41eb-914f-937a74fdd777 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=165f6e79-73ad-41eb-914f-937a74fdd777 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows 2000 Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=165f6e79-73ad-41eb-914f-937a74fdd777 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=37650e31-b428-40cd-b923-b9f12435cbac none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 369.0GB: boot/grub/menu.lst
 369.0GB: boot/grub/stage2
 365.3GB: boot/initrd.img-2.6.24-16-generic
 365.2GB: boot/initrd.img-2.6.24-16-generic.bak
 365.2GB: boot/initrd.img-2.6.24-17-generic
 365.2GB: boot/initrd.img-2.6.24-17-generic.bak
 365.3GB: boot/initrd.img-2.6.24-18-generic
 365.3GB: boot/initrd.img-2.6.24-18-generic.bak
 365.3GB: boot/initrd.img-2.6.24-19-generic
 365.3GB: boot/initrd.img-2.6.24-19-generic.bak
 365.2GB: boot/vmlinuz-2.6.24-16-generic
 365.2GB: boot/vmlinuz-2.6.24-17-generic
 365.2GB: boot/vmlinuz-2.6.24-18-generic
 365.3GB: boot/vmlinuz-2.6.24-19-generic
 365.3GB: initrd.img
 365.3GB: initrd.img.old
 365.3GB: vmlinuz
 365.2GB: vmlinuz.old

=======Devices which don't seem to have a corresponding hard drive==============

 sdb .

```

---

### Post by caljohnsmith on 2009-02-08
Are you getting the Grub error 21 after seeing the Grub menu on start up when you select Ubuntu to boot? Based on the results of the script, that's what it looks like is happening, but I just wanted to confirm you at least see the Grub menu on start up. If that's true, how about doing the following from your Live CD:
```
sudo mount /dev/sda6 /mnt && gksudo gedit /mnt/boot/grub/menu.lst
```
And then change all your Ubuntu entries to use (hd0,5) rather than (hd1,0) similar to:
```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		[COLOR="Blue"](hd0,5)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=165f6e79-73ad-41eb-914f-937a74fdd777 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```
Also change the "# groot=(hd1,0)" line:
```
# groot=[COLOR="Blue"](hd0,5)[/COLOR]
```
And by the way, I notice that you have a large ~123 GB of free space after your sda1 FAT32 partition, and also you are missing your swap partition. Therefore, while you are on the Live CD, I would recommend pulling up gparted (System > Admin > Partition Editor), and resizing the beginning of the sda2 extended partition so that it comes right after the end of sda1; then in that free space inside sda2 you can create logical partitions for swap, and maybe use the rest of the space for a data partition (or whatever other partitions you want, that's only a suggestion). Once you've created your partitions, quit gparted, go back to the terminal and run:
```
sudo fdisk -lu
```
Find which is your new swap partition as /dev/sdaX (like sda7 for example) and do:
```
sudo mkswap -U 37650e31-b428-40cd-b923-b9f12435cbac /dev/[COLOR="Blue"]sdaX[/COLOR]
```
That will change the UUID of the new swap partition to what your Ubuntu install was previously using as the UUID for swap, so that way you don't have to reconfigure any of Ubuntu's system files to use a new swap UUID. Then reboot, and let us know how far you get. We can work from there. :)

---

### Post by casparov on 2009-02-09
EUREKA!!!!  

(That would belong to you, CalJohn...)

Well, I don't know how you do it--all those command lines were from the outer limits of system nomenclature to me.  What superb work you did here--there was NO WAY I could have hashed all that out, no way...  

I took far too long to get to things--like everyone, things are taking pieces of me at this time.  But having Ubuntu restored successfully was a nice mental boost amid all else.  

Your long command line worked like a charm and directed GRUB to search for its files on the correct drive.  (I neglected to edit the "#groot=", but your changes generated a successful boot.)  I did not use the live CD to launch GParted and will make the changes you suggested (which amount to shrinking the proportionally enlarged W98 partition on the new SATA drive--I don't have any use for that, anyway).  The upshot is that I will have alot (123GB) of unallocated space, somewhere.  I will slide the NTFS partition against the W98 partition.  (I haven't played w/ GParted very much but assume that I can shift things around that I can significantly enlarge my W2KSP4 that much.  Also, I will make a swap partition of a few GB, as you suggest.)

I hadn't logged onto Ubuntu in at least 6 mos. so the 8.04 update was significant.  Ubuntu recognized the new video card perfectly but the sound was gone in all apps.  I set the sound setting to run on (I can't remember now--begins w/ an a) one of the basic options and the volume seems quite low.  But sound was missing entirely if set to "auto" and on a couple of the others.  (My card is a Sound Blaster Audigy 2.)  There is a lot of tweaking to do. 

I hope this thread helps a lot of others--I am at a loss for words to describe your assistance and how you kept at all this.  

You are amazing,

Casp

---

### Post by caljohnsmith on 2009-02-09
> **casparov said:**
> (I neglected to edit the "#groot=", but your changes generated a successful boot.)
I'm really glad to hear you can boot OK again. Just one small suggestion though: I would recommend changing the "#groot..." line in your menu.lst, because if you don't, the next time you get a kernel upgrade all your Ubuntu entries will be changed back to using (hd1,0) and you won't be able to boot again. Anyway, hope your partition changes go smoothly once you get around to doing them. Cheers and enjoy your Ubuntu install. :)

---

### Post by casparov on 2009-02-10
CalJohn... 

Your last injunction regarding "# groot=(hd0,1)" came in the nick of time because I corrected it just prior to upgrading to 8.10.  From what you indicated, I would have been faced w/ another black screen...  

Thanks so much again, 

Casp

---

### Post by dbld on 2010-06-03
hope caljohnsith would able to figure what is wrong with my installation.

i'm sending this from live CD as no grub gets loaded at all.

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Syslinux is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ubuntu/winboot/menu.lst /boot.ini /ntldr 
                       /NTDETECT.COM /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/winboot/wubildr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdd1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdd1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /COMMAND.COM

sde2: _________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x541fec16

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   268,414,019   268,413,957   7 HPFS/NTFS
/dev/sda2         268,414,020   312,576,704    44,162,685   5 Extended
/dev/sda5         268,414,083   310,648,904    42,234,822  83 Linux
/dev/sda6         310,648,968   312,576,704     1,927,737  82 Linux swap / Solaris
/dev/sda4         312,576,705   971,530,874   658,954,170   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2ba8c139

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,773,167   976,773,105  42 SFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x27f227f1

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   268,414,019   268,413,957   7 HPFS/NTFS
/dev/sdc2         268,414,020   308,383,739    39,969,720  83 Linux
/dev/sdc3         308,383,740   312,576,704     4,192,965  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 8127 MB, 8127512576 bytes
251 heads, 62 sectors/track, 1020 cylinders, total 15874048 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             62    15,873,239    15,873,178   c W95 FAT32 (LBA)


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2f982f97

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *      2,859,570    66,685,814    63,826,245   c W95 FAT32 (LBA)
/dev/sde2          66,685,815    78,140,159    11,454,345   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        229407BB94079089                       ntfs                                     
/dev/sda4        9A789F62789F3C47                       ntfs       largeBin                      
/dev/sda5        c2c1703c-7c76-450a-8aeb-e6424556d58d   ext3                                     
/dev/sda6        1455bacc-ca2e-4bc8-83da-3a37890cd548   swap                                     
/dev/sdc1        229407BB94079089                       ntfs                                     
/dev/sdc2        99811be2-eb48-4787-ab6f-3c29f82db97c   ext3                                     
/dev/sdc3        8917ca66-9971-4ef3-b6ca-c7a54e85773b   swap                                     
/dev/sdd1        1320-A189                              vfat                                     
/dev/sde1        9CF2-5D5F                              vfat       RESCUE                        
/dev/sde2        ca70edfa-5c0f-3ee1-85c1-549ad20f9b35   hfsplus    iATKOS v7                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdd1        /cdrom                   vfat       (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sde2        /media/iATKOS v7         hfsplus    (rw,nosuid,nodev,uhelper=devkit)
/dev/sde1        /media/RESCUE            vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda5        /media/c2c1703c-7c76-450a-8aeb-e6424556d58d ext3       (rw,nosuid,nodev,uhelper=devkit)
/dev/sda4        /media/largeBin          fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


======================== sda1/ubuntu/winboot/menu.lst: ========================

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

================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn /usepmtimer



C:\tboot=Mac Os X System


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
# kopt=root=UUID=c2c1703c-7c76-450a-8aeb-e6424556d58d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c2c1703c-7c76-450a-8aeb-e6424556d58d

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

title		Ubuntu 9.10, kernel 2.6.31-21-generic
uuid		c2c1703c-7c76-450a-8aeb-e6424556d58d
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=c2c1703c-7c76-450a-8aeb-e6424556d58d ro quiet splash 
initrd		/boot/initrd.img-2.6.31-21-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-21-generic (recovery mode)
uuid		c2c1703c-7c76-450a-8aeb-e6424556d58d
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=c2c1703c-7c76-450a-8aeb-e6424556d58d ro  single
initrd		/boot/initrd.img-2.6.31-21-generic

title		Ubuntu 9.10, kernel 2.6.31-20-generic
uuid		c2c1703c-7c76-450a-8aeb-e6424556d58d
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=c2c1703c-7c76-450a-8aeb-e6424556d58d ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid		c2c1703c-7c76-450a-8aeb-e6424556d58d
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=c2c1703c-7c76-450a-8aeb-e6424556d58d ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		c2c1703c-7c76-450a-8aeb-e6424556d58d
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=c2c1703c-7c76-450a-8aeb-e6424556d58d ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		c2c1703c-7c76-450a-8aeb-e6424556d58d
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=c2c1703c-7c76-450a-8aeb-e6424556d58d ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		c2c1703c-7c76-450a-8aeb-e6424556d58d
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=c2c1703c-7c76-450a-8aeb-e6424556d58d ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		c2c1703c-7c76-450a-8aeb-e6424556d58d
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=c2c1703c-7c76-450a-8aeb-e6424556d58d ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		c2c1703c-7c76-450a-8aeb-e6424556d58d
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=c2c1703c-7c76-450a-8aeb-e6424556d58d ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		c2c1703c-7c76-450a-8aeb-e6424556d58d
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=c2c1703c-7c76-450a-8aeb-e6424556d58d ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic
uuid		c2c1703c-7c76-450a-8aeb-e6424556d58d
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=c2c1703c-7c76-450a-8aeb-e6424556d58d ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid		c2c1703c-7c76-450a-8aeb-e6424556d58d
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=c2c1703c-7c76-450a-8aeb-e6424556d58d ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, memtest86+
uuid		c2c1703c-7c76-450a-8aeb-e6424556d58d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title		Microsoft Windows XP Professional
rootnoverify	(hd3,0)
savedefault
makeactive
map		(hd0) (hd3)
map		(hd3) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd2.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (on /dev/sdd2)
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=99811be2-eb48-4787-ab6f-3c29f82db97c ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd2.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode) (on /dev/sdd2)
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=99811be2-eb48-4787-ab6f-3c29f82db97c ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd2.
title		Ubuntu 8.04, kernel 2.6.22-14-generic (on /dev/sdd2)
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=99811be2-eb48-4787-ab6f-3c29f82db97c ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd2.
title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode) (on /dev/sdd2)
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=99811be2-eb48-4787-ab6f-3c29f82db97c ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd2.
title		Ubuntu 8.04, kernel 2.6.20-16-generic (on /dev/sdd2)
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=99811be2-eb48-4787-ab6f-3c29f82db97c ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd2.
title		Ubuntu 8.04, kernel 2.6.20-16-generic (recovery mode) (on /dev/sdd2)
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=99811be2-eb48-4787-ab6f-3c29f82db97c ro single 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd2.
title		Ubuntu 8.04, kernel 2.6.20-15-generic (on /dev/sdd2)
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=99811be2-eb48-4787-ab6f-3c29f82db97c ro quiet splash 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd2.
title		Ubuntu 8.04, kernel 2.6.20-15-generic (recovery mode) (on /dev/sdd2)
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=99811be2-eb48-4787-ab6f-3c29f82db97c ro single 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd2.
title		Ubuntu 8.04, memtest86+ (on /dev/sdd2)
root		(hd3,1)
kernel		/boot/memtest86+.bin  
savedefault
boot


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=c2c1703c-7c76-450a-8aeb-e6424556d58d /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=1455bacc-ca2e-4bc8-83da-3a37890cd548 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 149.3GB: boot/grub/menu.lst
 149.1GB: boot/grub/stage2
 149.0GB: boot/initrd.img-2.6.28-16-generic
 149.3GB: boot/initrd.img-2.6.31-14-generic
 149.4GB: boot/initrd.img-2.6.31-15-generic
 151.8GB: boot/initrd.img-2.6.31-16-generic
 149.7GB: boot/initrd.img-2.6.31-20-generic
 153.4GB: boot/initrd.img-2.6.31-21-generic
 152.5GB: boot/vmlinuz-2.6.28-16-generic
 149.6GB: boot/vmlinuz-2.6.31-14-generic
 149.4GB: boot/vmlinuz-2.6.31-15-generic
 148.9GB: boot/vmlinuz-2.6.31-16-generic
 153.7GB: boot/vmlinuz-2.6.31-20-generic
 153.4GB: boot/vmlinuz-2.6.31-21-generic
 153.4GB: initrd.img
 149.7GB: initrd.img.old
 153.4GB: vmlinuz
 153.7GB: vmlinuz.old

================================ sdc1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn


=========================== sdc2/boot/grub/menu.lst: ===========================

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=99811be2-eb48-4787-ab6f-3c29f82db97c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=99811be2-eb48-4787-ab6f-3c29f82db97c ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=99811be2-eb48-4787-ab6f-3c29f82db97c ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=99811be2-eb48-4787-ab6f-3c29f82db97c ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=99811be2-eb48-4787-ab6f-3c29f82db97c ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, kernel 2.6.20-16-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=99811be2-eb48-4787-ab6f-3c29f82db97c ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=99811be2-eb48-4787-ab6f-3c29f82db97c ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 8.04, kernel 2.6.20-15-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=99811be2-eb48-4787-ab6f-3c29f82db97c ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet

title		Ubuntu 8.04, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=99811be2-eb48-4787-ab6f-3c29f82db97c ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sdc2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=99811be2-eb48-4787-ab6f-3c29f82db97c /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc5
UUID=BAF8DBF6F8DBAF3F /media/hdc5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=229407BB94079089 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=8917ca66-9971-4ef3-b6ca-c7a54e85773b none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

=================== sdc2: Location of files loaded by Grub: ===================


 154.7GB: boot/grub/menu.lst
 154.3GB: boot/grub/stage2
 154.3GB: boot/initrd.img-2.6.20-15-generic
 154.4GB: boot/initrd.img-2.6.20-15-generic.bak
 154.4GB: boot/initrd.img-2.6.20-16-generic
 154.4GB: boot/initrd.img-2.6.20-16-generic.bak
 154.3GB: boot/initrd.img-2.6.22-14-generic
 154.3GB: boot/initrd.img-2.6.22-14-generic.bak
 154.9GB: boot/initrd.img-2.6.24-16-generic
 154.7GB: boot/initrd.img-2.6.24-16-generic.bak
 154.4GB: boot/vmlinuz-2.6.20-15-generic
 154.4GB: boot/vmlinuz-2.6.20-16-generic
 154.4GB: boot/vmlinuz-2.6.22-14-generic
 141.3GB: boot/vmlinuz-2.6.24-16-generic
 154.9GB: initrd.img
 154.3GB: initrd.img.old
 141.3GB: vmlinuz
 154.4GB: vmlinuz.old

================================ sde1/boot.ini: ================================

[boot loader]

timeout=0

default=C:\

[operating systems]

multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\ = "PC-DOS"

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1


Unknown BootLoader  on sde2

00000000  fa 31 c0 8e d0 bc f0 ff  fb 8e c0 8e d8 b0 48 e8  |.1............H.|
00000010  3d 01 66 8b 44 08 e8 54  01 66 31 c0 66 a3 00 e4  |=.f.D..T.f1.f...|
00000020  80 7c 04 af 75 03 e9 09  00 be a6 7d e8 10 01 e9  |.|..u......}....|
00000030  c2 00 b0 5d e8 18 01 b0  01 31 db 8e c3 bb 00 14  |...].....1......|
00000040  66 b9 02 00 00 00 e8 ae  00 73 03 e9 9b 00 a1 00  |f........s......|
00000050  14 3d 42 44 75 3f b0 7c  e8 f4 00 66 8b 1e 14 14  |.=BDu?.|...f....|
00000060  66 0f cb 66 c1 fb 09 66  31 c0 a1 7e 14 86 c4 52  |f..f...f1..~...R|
00000070  66 f7 e3 5a 66 31 db 8b  1e 1c 14 86 df 66 01 d8  |f..Zf1.......f..|
00000080  66 40 66 40 66 89 c1 b0  01 31 db 8e c3 bb 00 14  |f@f@f....1......|
00000090  e8 64 00 72 54 b0 7d e8  b5 00 a1 00 14 3d 48 2b  |.d.rT.}......=H+|
000000a0  74 05 3d 48 58 75 42 b0  2a e8 a3 00 66 a1 28 14  |t.=HXuB.*...f.(.|
000000b0  66 0f c8 66 c1 f8 09 66  8b 1e c0 15 66 0f cb 52  |f..f...f....f..R|
000000c0  66 f7 e3 5a 66 48 66 48  66 01 c1 b0 21 e8 7f 00  |f..ZfHfHf...!...|
000000d0  b0 7e bb 00 20 8e c3 bb  00 02 e8 1a 00 72 0a b0  |.~.. ........r..|
000000e0  59 e8 6b 00 ea 00 02 00  20 be bd 7d e8 50 00 b0  |Y.k..... ..}.P..|
000000f0  58 e8 5b 00 f4 eb fd 66  60 89 e5 1e 1e 66 03 0e  |X.[....f`....f..|
00000100  00 e4 66 03 4c 08 66 51  06 53 30 e4 50 50 b0 2d  |..f.L.fQ.S0.PP.-|
00000110  e8 3c 00 66 89 c8 e8 54  00 b0 3d e8 31 00 58 e8  |.<.f...T..=.1.X.|
00000120  4b 00 68 10 00 89 e6 b4  42 cd 13 73 0d e8 3d 00  |K.h.....B..s..=.|
00000130  b0 52 e8 1a 00 31 c0 cd  13 f9 89 ec 66 61 c3 bb  |.R...1......fa..|
00000140  01 00 fc ac 3c 00 74 06  b4 0e cd 10 eb f5 c3 66  |....<.t........f|
00000150  60 bb 01 00 b4 0e cd 10  66 61 c3 66 60 31 c9 88  |`.......fa.f`1..|
00000160  c1 b0 20 e3 05 e8 e7 ff  e2 f9 66 61 c3 66 60 b9  |.. .......fa.f`.|
00000170  04 00 66 0f c8 50 c0 c8  04 e8 17 00 58 e8 13 00  |..f..P......X...|
00000180  66 c1 c8 08 e2 ef b0 0a  e8 c4 ff b0 0d e8 bf ff  |f...............|
00000190  66 61 c3 24 0f 04 30 3c  39 76 02 04 07 e8 af ff  |fa.$..0<9v......|
000001a0  c3 b4 00 cd 16 c3 0a 0d  48 46 53 2b 20 70 61 72  |........HFS+ par|
000001b0  74 69 74 69 6f 6e 20 65  72 72 6f 72 00 0a 0d 45  |tition error...E|
000001c0  72 72 6f 72 20 6c 6f 61  64 69 6e 67 20 62 6f 6f  |rror loading boo|
000001d0  74 65 72 00 00 00 00 00  00 00 00 00 00 00 00 00  |ter.............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdf 
=============================== StdErr Messages: ===============================

ERROR: asr: seeking device "/dev/sdf" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sdf" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sdf" to 18446744073709420032
ERROR: hpt37x: seeking device "/dev/sdf" to 4608
ERROR: hpt45x: seeking device "/dev/sdf" to 18446744073709545984
ERROR: isw: seeking device "/dev/sdf" to 18446744073709550592
ERROR: isw: seeking device "/dev/sdf" to 18446744073709551104
ERROR: isw: seeking device "/dev/sdf" to 18446744073708468736
ERROR: jmicron: seeking device "/dev/sdf" to 18446744073709551104
ERROR: lsi: seeking device "/dev/sdf" to 18446744073709551104
ERROR: nvidia: seeking device "/dev/sdf" to 18446744073709550592
ERROR: pdc: seeking device "/dev/sdf" to 137438913024
ERROR: pdc: seeking device "/dev/sdf" to 137438920192
ERROR: pdc: seeking device "/dev/sdf" to 137438927360
ERROR: pdc: seeking device "/dev/sdf" to 137438934528
ERROR: sil: seeking device "/dev/sdf" to 18446744073709551104
ERROR: via: seeking device "/dev/sdf" to 18446744073709551104
ERROR: asr: seeking device "/dev/sdf" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sdf" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sdf" to 18446744073709420032
ERROR: hpt37x: seeking device "/dev/sdf" to 4608
ERROR: hpt45x: seeking device "/dev/sdf" to 18446744073709545984
ERROR: isw: seeking device "/dev/sdf" to 18446744073709550592
ERROR: isw: seeking device "/dev/sdf" to 18446744073709551104
ERROR: isw: seeking device "/dev/sdf" to 18446744073708468736
ERROR: jmicron: seeking device "/dev/sdf" to 18446744073709551104
ERROR: lsi: seeking device "/dev/sdf" to 18446744073709551104
ERROR: nvidia: seeking device "/dev/sdf" to 18446744073709550592
ERROR: pdc: seeking device "/dev/sdf" to 137438913024
ERROR: pdc: seeking device "/dev/sdf" to 137438920192
ERROR: pdc: seeking device "/dev/sdf" to 137438927360
ERROR: pdc: seeking device "/dev/sdf" to 137438934528
ERROR: sil: seeking device "/dev/sdf" to 18446744073709551104
ERROR: via: seeking device "/dev/sdf" to 18446744073709551104
hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb1: No such file or directory

```

---

### Post by kansasnoob on 2010-06-03
First of all a quick review of what you have. I see 4 operating systems:

Win XP on sda1
Ubuntu 9.10 w/legacy grub on sda5
Win XP on sdc1
Ubuntu 8.04 on sdc2

Both sda and sdc have a Windows MBR:

>  => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

Also sda is a 500GB drive and sdc is 160GB. We won't worry about the other drives as they have no operating systems installed.

The 9.10 (sda5) menu.lst has some problems:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/**[COLOR="Red"]sdd1[/COLOR]**
title		Microsoft Windows XP Professional
rootnoverify	**[COLOR="Red"](hd3,0)[/COLOR]**
savedefault
makeactive
map		(hd0) **[COLOR="Red"](hd3)[/COLOR]**
map		**[COLOR="Red"](hd3)[/COLOR]** (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/**[COLOR="Red"]sdd2[/COLOR]**.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (on /dev/**[COLOR="Red"]sdd2[/COLOR]**)
root		**[COLOR="Red"](hd3,1)[/COLOR]**
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=99811be2-eb48-4787-ab6f-3c29f82db97c ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd2.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode) (on /dev/sdd2)
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=99811be2-eb48-4787-ab6f-3c29f82db97c ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd2.
title		Ubuntu 8.04, kernel 2.6.22-14-generic (on /dev/sdd2)
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=99811be2-eb48-4787-ab6f-3c29f82db97c ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd2.
title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode) (on /dev/sdd2)
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=99811be2-eb48-4787-ab6f-3c29f82db97c ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd2.
title		Ubuntu 8.04, kernel 2.6.20-16-generic (on /dev/sdd2)
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=99811be2-eb48-4787-ab6f-3c29f82db97c ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd2.
title		Ubuntu 8.04, kernel 2.6.20-16-generic (recovery mode) (on /dev/sdd2)
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=99811be2-eb48-4787-ab6f-3c29f82db97c ro single 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd2.
title		Ubuntu 8.04, kernel 2.6.20-15-generic (on /dev/sdd2)
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=99811be2-eb48-4787-ab6f-3c29f82db97c ro quiet splash 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd2.
title		Ubuntu 8.04, kernel 2.6.20-15-generic (recovery mode) (on /dev/sdd2)
root		(hd3,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=99811be2-eb48-4787-ab6f-3c29f82db97c ro single 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdd2.
title		Ubuntu 8.04, memtest86+ (on /dev/sdd2)
root		(hd3,1)
kernel		/boot/memtest86+.bin  
savedefault
boot

```

I only highlighted a few examples, but it appears that you switched drives around at some point :confused:

The 8.04 (sdc2) menu.lst is hardly worth saving because it's drive was obviously at one time sdb (but the XP entries confuse even further):

> # groot=**[COLOR="Red"](hd1,1)[/COLOR]**

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/**[COLOR="Red"]sda1[/COLOR]**
title		Microsoft Windows XP Professional
root		**[COLOR="Red"](hd1,0)[/COLOR]**
savedefault
makeactive
map		**[COLOR="Red"](hd0) (hd1)[/COLOR]**
map		**[COLOR="Red"](hd1) (hd0)[/COLOR]**
chainloader	+1
```

It does look like the 9.10 menu.lst should boot 9.10 and the Win XP on sda (if it's still bootable) so the first thing I would do is make sure that "sda" (the 500GB drive) is set to boot first in BIOS. **That could be somewhat tricky because sda and sdb are both 500GB! **

Next boot a Live CD (9.04 or older) and in terminal:

```
sudo grub
```

```
root (hd0,4)
```

```
setup (hd0)
```

If correct you should see an output like:
&#65279;
> Checking if "/boot/grub/stage1" exists... **[COLOR="Red"]yes[/COLOR]**
Checking if "/boot/grub/stage2" exists... **[COLOR="Red"]yes[/COLOR]**
Checking if "/boot/grub/e2fs_stage1_5" exists... **[COLOR="Red"]yes[/COLOR]**
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...* 15 sectors are embedded.
**[COLOR="Red"]succeeded[/COLOR]**
Running "install /boot/grub/stage1 d (hd0) (hd0)1+15 p (hd0,1)/boot/grub/stage
2 /boot/grub/menu.lst"... **[COLOR="Red"]succeeded[/COLOR]**
Done. 

So then just:

```
quit
```

Hopefully that will boot 9.10. If not I'd suspect that you have the wrong drive set to boot first in BIOS.

If you can get 9.10 booted that way then you could either spend a lot of time correcting the entries in it's menu.lst or you could upgrade to grub 2.

If you can boot into 9.10 after running the above commands and want to try upgrading to grub 2 then run the following **while booted into 9.10**:

```
sudo mv /boot/grub /boot/grub_legacy
```

```
sudo mkdir /boot/grub
```

```
sudo apt-get --purge remove startupmanager
```

Note: if not installed it will just tell you so, regardless proceed:

```
sudo apt-get --purge remove grub grub-common
```

```
sudo apt-get install grub-pc
```

```
sudo apt-get install --reinstall os-prober
```

Note: os-prober should be installed anyway but we're just making sure so continue:

```
sudo update-grub
```

Note: Wait for that to say done, then:

```
sudo grub-install /dev/sda
```

Note: If that returns any errors also run:

```
sudo grub-install --recheck /dev/sda
```

Hopefully that's it, but grub 2 is a different beast:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by dbld on 2010-06-04
Hi kansasnoob, 

ty for the elaborate analysis and suggestions. i know my installation looks a mess. 

as you have suggested, I initially attempted to use the grub to rebuild the mbr but it as failing with the error that appears int the heading of this thread "GRUB Error 21: Selected Disk Does Not Exist..."

Thus my post... 

Subsequent to your reply, i have attempted the same again, this time it was successful..   yay

Now i'm of to clean up and upgrade to grub 2 as you suggested.

so once again ty for the prompt and elaborate response..

---

### Post by kansasnoob on 2010-06-04
> **dbld said:**
> Hi kansasnoob, 

ty for the elaborate analysis and suggestions. i know my installation looks a mess. 

as you have suggested, I initially attempted to use the grub to rebuild the mbr but it as failing with the error that appears int the heading of this thread "GRUB Error 21: Selected Disk Does Not Exist..."

Thus my post... 

Subsequent to your reply, i have attempted the same again, this time it was successful..   yay

Now i'm of to clean up and upgrade to grub 2 as you suggested.

so once again ty for the prompt and elaborate response..

So, some progress? Keep us posted and if something fails please post the full terminal output of the failure so we can try to troubleshoot it.

Or at the very least run the Boot Info Script again and post the newest results. At the very end of running the script it will show you what the new output is named, eg: RESULTS**1**.txt, RESULTS**2**.txt, etc.

---

