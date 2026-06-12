---
title: "Grub with Different Disks"
date: 2009-08-28
forum: Installation &amp; Upgrades
---

### Post by snm_cal on 2009-08-28
I've 3 hdd in my machine. I've installed all of them in a stand alone manner. They have Xubuntu Jaunty, Vista and XP. I can boot in any one of them by adjusting the bios.

Now, I'm trying to edit my grub in such a manner that I can boot in any one of them. Obviously I'm planning to have the Xubuntu disk at the first at bios.

This is the output of fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb9976003

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3917    31463271    7  HPFS/NTFS
/dev/sda2            3918       19457   124825050    5  Extended
/dev/sda5            3918        7834    31463271    7  HPFS/NTFS
/dev/sda6            7835       19457    93361713    7  HPFS/NTFS

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008eaff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9964    80035798+   7  HPFS/NTFS

Disk /dev/sdc: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x883b3423

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        2327    18691596   83  Linux
/dev/sdc2            2328        2434      859477+   5  Extended
/dev/sdc5            2328        2434      859446   82  Linux swap / Solaris

This is my menu.lst

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        18ed2034-0a09-4fc9-968c-66ab877ad1d9
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=18ed2034-0a09-4fc9-968c-66ab877ad1d9 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

#title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
#uuid        18ed2034-0a09-4fc9-968c-66ab877ad1d9
#kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=18ed2034-0a09-4fc9-968c-66ab877ad1d9 ro  single
#initrd        /boot/initrd.img-2.6.28-15-generic

#title        Ubuntu 9.04, kernel 2.6.28-11-generic
#uuid        18ed2034-0a09-4fc9-968c-66ab877ad1d9
#kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=18ed2034-0a09-4fc9-968c-66ab877ad1d9 ro quiet splash 
#initrd        /boot/initrd.img-2.6.28-11-generic
#quiet

#title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
#uuid        18ed2034-0a09-4fc9-968c-66ab877ad1d9
#kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=18ed2034-0a09-4fc9-968c-66ab877ad1d9 ro  single
#initrd        /boot/initrd.img-2.6.28-11-generic

#title        Ubuntu 9.04, memtest86+
#uuid        18ed2034-0a09-4fc9-968c-66ab877ad1d9
#kernel        /boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title        Other operating systems:
#root


#This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows Vista
rootnoverify    (hd2,0)
makeactive
#savedefault
chainloader    +1

title        Microsoft Windows XP Professional
rootnoverify    (hd1,0)
makeactive
#savedefault
chainloader    +1

I can boot to Vista smmothly through Grub, but not to XP. IT says, "Starting....."
and then keeps mum.

I'm a newbie in Ubuntu. Can anyone please help me? Thanks a lot in advance.

---

### Post by hal10000 on 2009-08-28
You should not need to make any changes in the bios to boot. I'm a bit confused, because the listings of fdisk -l contradicts with your menu.lst.
This may be caused by changing the boot-order in th bios.
But I guess your windows XP resides in the 160 GB disk?
If so, then you should change this part of your /boot/grub/menu.lst file:> title Microsoft Windows XP Professional
rootnoverify (hd1,0)
makeactive
#savedefault
chainloader +1
into 
> title Microsoft Windows XP Professional
rootnoverify (hd[COLOR="Red"]0[/COLOR],0)
makeactive
#savedefault
chainloader +1
This is only valid, if you didn't change the bios-settings since you posted this.

---

### Post by snm_cal on 2009-08-28
Thanks a lot for the reply, hal10000.

I tell you the exact situation. My board is intel 965ryck. 2 Ide and 4 SATA channels.

I've 
20 G at IDE Master, 1 partition, has the Xubuntu
160G in SATA 0, has 3 partitions, has xp at partition 1
80G in SATA 1, has 1 partition, has vista.

Bios Drive order is, 20G, 160G, 80G.

When Xubuntu boots, it boots from (hd0,0), ext3

Tried (hd0,0) earlier, it says something like "unsupported system".

Tried (hd3,0), (hd4,0) .... they say "no disk".

I think, (hd1,0) is finding the xp drive but remaining unable to boot. Is there any special command in grub for xp itself?

Thanks a lot again for your time and advise.

---

### Post by presence1960 on 2009-08-28
Let's get a better look at your setup. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

Also can you go into BIOS and let us know the boot order of your hard disks please.

---

### Post by snm_cal on 2009-08-29
Thank you, presence1960.

Here is the results.txt
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

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
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 69. But according to the info from fdisk, 
                       sda6 starts at sector 125853279.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb9976003

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    62,926,604    62,926,542   7 HPFS/NTFS
/dev/sda2          62,926,605   312,576,704   249,650,100   5 Extended
/dev/sda5          62,926,668   125,853,209    62,926,542   7 HPFS/NTFS
/dev/sda6         125,853,279   312,576,704   186,723,426   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0008eaff

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   160,071,659   160,071,597   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x883b3423

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    37,383,254    37,383,192  83 Linux
/dev/sdc2          37,383,255    39,102,209     1,718,955   5 Extended
/dev/sdc5          37,383,318    39,102,209     1,718,892  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="CA202D7C202D709D" TYPE="ntfs" 
/dev/sda5: UUID="D1914CC6A5834AC5" TYPE="ntfs" 
/dev/sda6: UUID="A2DF45AFA892DCAD" TYPE="ntfs" 
/dev/sdb1: UUID="D840B7B040B7942A" TYPE="ntfs" 
/dev/sdc1: UUID="18ed2034-0a09-4fc9-968c-66ab877ad1d9" TYPE="ext3" 
/dev/sdc5: TYPE="swap" UUID="888d4675-0ac3-4582-931f-ce44ef3f33a5" 

=============================== "mount" output: ===============================

/dev/sdc1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
/dev/sda6 on /media/E: type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /media/D: type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/C: type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdc1/boot/grub/menu.lst: ===========================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

Pretty colours
color cyan/blue white/blue

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=18ed2034-0a09-4fc9-968c-66ab877ad1d9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=18ed2034-0a09-4fc9-968c-66ab877ad1d9

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        18ed2034-0a09-4fc9-968c-66ab877ad1d9
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=18ed2034-0a09-4fc9-968c-66ab877ad1d9 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

#title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
#uuid        18ed2034-0a09-4fc9-968c-66ab877ad1d9
#kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=18ed2034-0a09-4fc9-968c-66ab877ad1d9 ro  single
#initrd        /boot/initrd.img-2.6.28-15-generic

#title        Ubuntu 9.04, kernel 2.6.28-11-generic
#uuid        18ed2034-0a09-4fc9-968c-66ab877ad1d9
#kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=18ed2034-0a09-4fc9-968c-66ab877ad1d9 ro quiet splash 
#initrd        /boot/initrd.img-2.6.28-11-generic
#quiet

#title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
#uuid        18ed2034-0a09-4fc9-968c-66ab877ad1d9
#kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=18ed2034-0a09-4fc9-968c-66ab877ad1d9 ro  single
#initrd        /boot/initrd.img-2.6.28-11-generic

#title        Ubuntu 9.04, memtest86+
#uuid        18ed2034-0a09-4fc9-968c-66ab877ad1d9
#kernel        /boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title        Other operating systems:
#root


#This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows Vista
rootnoverify    (hd2,0)
makeactive
#savedefault
chainloader    +1

title        Microsoft Windows XP Professional
root        (hd1,0)
makeactive
#savedefault
chainloader    +1



=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdb1 :
UUID=18ed2034-0a09-4fc9-968c-66ab877ad1d9 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sdb5 :
UUID=888d4675-0ac3-4582-931f-ce44ef3f33a5 none swap sw 0 0
/dev/sda6 /media/E: ntfs-3g defaults,locale=en_IN 0 0
/dev/sda5 /media/D: ntfs-3g defaults,locale=en_IN 0 0
/dev/sda1 /media/C: ntfs-3g defaults,locale=en_IN 0 0

=================== sdc1: Location of files loaded by Grub: ===================


  11.5GB: boot/grub/menu.lst
  11.4GB: boot/grub/stage2
  11.4GB: boot/initrd.img-2.6.28-11-generic
  11.5GB: boot/initrd.img-2.6.28-15-generic
  11.4GB: boot/vmlinuz-2.6.28-11-generic
  11.4GB: boot/vmlinuz-2.6.28-15-generic
  11.5GB: initrd.img
  11.4GB: initrd.img.old
  11.4GB: vmlinuz
  11.4GB: vmlinuz.old
```My hdd and bios order are

20 G at IDE Master, 1 partition, has the Xubuntu
160G in SATA 0, has 3 partitions, has xp at partition 1
80G in SATA 1, has 1 partition, has vista.

Bios Drive order is, 20G, 160G, 80G.

Thanks a lot again.

---

### Post by hal10000 on 2009-08-29
This boot_info_script is a very fine thing.

But I think we have a very mysterious problem here. I will try to summarize the situation:
1.) You say your BIOS drive order is 20GB IDE disk (Xubuntu) - 160GB SATA disk (Windows XP) - 80GB SATA disk (Vista)
2.) You can currently boot Vista, but not XP, is this right?
3.) The entries in your menu.lst file should be correct, according to boot_info_script, but it's not possible for you to boot XP
4.) You say, you can boot XP if you adjust the BIOS drive order.

I'm a bit confused because it should work with your settings. So, can you explain how you change the drive order and the steps you take to boot your systems?

I guess the main thing is, that we have three different kinds of notations for harddisk drives:
- UUID (which is used in modern Linux systems)
- /dev/sda, /dev/sdb etc. (which is the normal UNIX/Linux way for harddrives)
- (hd0), (hd1) etc. (which is the BSD-way for harddrives, and is also used by grub and windows, you can see this if you look into your boot.ini file in windows)

---

### Post by snm_cal on 2009-08-29
hal10000, Thanks a lot.

Let me explain,

1. In my bios, the drive orders are now 20G(Xubuntu), 160G(Xp), 80G(Vista)
         I can boot to xp if I change the order in 160G(xp) then any other.
         This rule follows for Vista too.

2. Yes I can boot vista through Grub, but for Xp it says "Starting...." and stalls there. But in the case of vista, the "Starting..." screen is going in a flash and the normal vista booting screen appears.

4. Yes, I can boot to xp, in fact I'm writing this reply from my xp system. I've also used chkdsk for any partition error in Xp boot (C:), but found none. The system is running smoothly.

If you don't mind and pardon my ignorance, I found something like "map (hd1, hd0)" like command in grub somewhere in the several posts. Does it have anything to do in this situation?


Thanks a lot again.

---

### Post by presence1960 on 2009-08-29
you need to edit your windows entries in menu.lst. Boot into Ubuntu and open a terminal and run this command ```
gksu gedit /boot/grub/menu.lst
``` I am not sure if Xubuntu has gedit, if not use whatever text editor xubuntu has. Change your windows entries to these:

> #This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Microsoft Windows Vista
rootnoverify    (hd2,0)
map             (hd0) (hd2)
map             (hd2) (hd0)   
chainloader     +1

#This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1

title        Microsoft Windows XP Professional
root         (hd1,0)
map          (hd0) (hd1)
map          (hd1) (hd0)
chainloader  +1

it is important to know a couple things. Firstly Windows will not boot unless it is on the first disk to boot in the hard drive boot order in BIOS. Your 20 GB HDD boots first so you need those map lines to "trick" windows into thinking it's drive is booting first.

Secondly when using root (hdx,y) or rootnoverify (hdx,y) designations you need to use the order of hard disk booting in BIOS not the results of fdisk. As you can see the results from fdisk show a different order of the disks than BIOS does. Unfortunately fdisk sometimes reads drive order differently than BIOS does. Because XP is on the second boot disk you will use (hd1,0) for XP and Vista is on the third disk to boot you will use (hd2,0).

I also run Sabayon 4.1 and on the install it has the option to set the order of disks as they are in BIOS or any way you prefer for that matter. maybe one day Ubuntu will have that option in it's installer.

---

### Post by hal10000 on 2009-08-29
When you change the boot-order to boot xp, then you boot directly into xp, i mean no grub menu appears, is that right?
The fact, that you can boot xp means also that xp is set up correctly, including boot.ini, ntldr etc.
So, the mistake can only reside in the /boot/grub/menu.lst file.
he only isea i have is to change the menu.lst file in the xp-section from
> 
title        Microsoft Windows XP Professional
root        (hd1,0)
makeactive
#savedefault
chainloader    +1

to
> 
title        Microsoft Windows XP Professional
rootnoverify  (hd1,0)
makeactive
#savedefault
chainloader    +1


I found this at [http://www.linuxjournal.com/article/4622](http://www.linuxjournal.com/article/4622) (...First, the rootnoverify command is for OS filesystems not specifically recognized by GRUB, so that GRUB will not try to mount the partition. Next, the chainloader ....)

---

### Post by presence1960 on 2009-08-29
> **hal10000 said:**
> When you change the boot-order to boot xp, then you boot directly into xp, i mean no grub menu appears, is that right?
The fact, that you can boot xp means also that xp is set up correctly, including boot.ini, ntldr etc.
So, the mistake can only reside in the /boot/grub/menu.lst file.
he only isea i have is to change the menu.lst file in the xp-section from

to


I found this at [http://www.linuxjournal.com/article/4622](http://www.linuxjournal.com/article/4622) (...First, the rootnoverify command is for OS filesystems not specifically recognized by GRUB, so that GRUB will not try to mount the partition. Next, the chainloader ....)

That will not work because windows is not on the first hard disk to boot. he must have the map lines in there for windows to boot from GRUB.

---

### Post by snm_cal on 2009-08-29
Thanks a lot presence1960 and hal10000.

I've just found the solution by some trial and error. It is related to the "map" command as presence1960 says.

Lets see my menu.lst first

```
title        Microsoft Windows Vista
rootnoverify    (hd2,0)
makeactive
#savedefault
chainloader    +1

title        Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
makeactive
#savedefault
chainloader    +1

```This is booting both the systems, in fact, all the 3 systems fine.

What I guess, Vista has the capability to get booted from a drive down in the bios order. Which Xp or 98 does not. In fact I found the solution from a 98 example. So the magic of map command comes into the picture.

I am going to try the way presence1960 has mentioned, And going to state the result asap.

Thanks a lot again for both of your precious time and effort.

Regards
Suvransu

---

### Post by presence1960 on 2009-08-29
Glad you got it working. Enjoy Ubuntu!

When you have time I would go over that results.txt file from the boot info script. it will reveal a lot about your setup and boot process. hopefully you can make the connection why the map lines are needed and work after studying the info.

---

### Post by snm_cal on 2009-08-29
presence1960,

Yes, enjoying Ubuntu a lot. Thanks a ton.

Your setting also works fine. But I'm giving the results.txt from the setting earlier. Understanding now why the map lines are needed. 

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

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
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 69. But according to the info from fdisk, 
                       sda6 starts at sector 125853279.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb9976003

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    62,926,604    62,926,542   7 HPFS/NTFS
/dev/sda2          62,926,605   312,576,704   249,650,100   5 Extended
/dev/sda5          62,926,668   125,853,209    62,926,542   7 HPFS/NTFS
/dev/sda6         125,853,279   312,576,704   186,723,426   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0008eaff

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   160,071,659   160,071,597   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x883b3423

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    37,383,254    37,383,192  83 Linux
/dev/sdc2          37,383,255    39,102,209     1,718,955   5 Extended
/dev/sdc5          37,383,318    39,102,209     1,718,892  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="CA202D7C202D709D" TYPE="ntfs" 
/dev/sda5: UUID="D1914CC6A5834AC5" TYPE="ntfs" 
/dev/sda6: UUID="A2DF45AFA892DCAD" TYPE="ntfs" 
/dev/sdb1: UUID="D840B7B040B7942A" TYPE="ntfs" 
/dev/sdc1: UUID="18ed2034-0a09-4fc9-968c-66ab877ad1d9" TYPE="ext3" 
/dev/sdc5: TYPE="swap" UUID="888d4675-0ac3-4582-931f-ce44ef3f33a5" 

=============================== "mount" output: ===============================

/dev/sdc1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
/dev/sda6 on /media/E: type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /media/D: type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/C: type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdc1/boot/grub/menu.lst: ===========================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

Pretty colours
color cyan/blue white/blue

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=18ed2034-0a09-4fc9-968c-66ab877ad1d9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=18ed2034-0a09-4fc9-968c-66ab877ad1d9

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        18ed2034-0a09-4fc9-968c-66ab877ad1d9
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=18ed2034-0a09-4fc9-968c-66ab877ad1d9 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

#title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
#uuid        18ed2034-0a09-4fc9-968c-66ab877ad1d9
#kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=18ed2034-0a09-4fc9-968c-66ab877ad1d9 ro  single
#initrd        /boot/initrd.img-2.6.28-15-generic

#title        Ubuntu 9.04, kernel 2.6.28-11-generic
#uuid        18ed2034-0a09-4fc9-968c-66ab877ad1d9
#kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=18ed2034-0a09-4fc9-968c-66ab877ad1d9 ro quiet splash 
#initrd        /boot/initrd.img-2.6.28-11-generic
#quiet

#title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
#uuid        18ed2034-0a09-4fc9-968c-66ab877ad1d9
#kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=18ed2034-0a09-4fc9-968c-66ab877ad1d9 ro  single
#initrd        /boot/initrd.img-2.6.28-11-generic

#title        Ubuntu 9.04, memtest86+
#uuid        18ed2034-0a09-4fc9-968c-66ab877ad1d9
#kernel        /boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title        Other operating systems:
#root


#This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows Vista
rootnoverify    (hd2,0)
makeactive
#savedefault
chainloader    +1

title        Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
makeactive
#savedefault
chainloader    +1



=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdb1 :
UUID=18ed2034-0a09-4fc9-968c-66ab877ad1d9 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sdb5 :
UUID=888d4675-0ac3-4582-931f-ce44ef3f33a5 none swap sw 0 0
/dev/sda6 /media/E: ntfs-3g defaults,locale=en_IN 0 0
/dev/sda5 /media/D: ntfs-3g defaults,locale=en_IN 0 0
/dev/sda1 /media/C: ntfs-3g defaults,locale=en_IN 0 0

=================== sdc1: Location of files loaded by Grub: ===================


  11.5GB: boot/grub/menu.lst
  11.4GB: boot/grub/stage2
  11.4GB: boot/initrd.img-2.6.28-11-generic
  11.5GB: boot/initrd.img-2.6.28-15-generic
  11.4GB: boot/vmlinuz-2.6.28-11-generic
  11.4GB: boot/vmlinuz-2.6.28-15-generic
  11.5GB: initrd.img
  11.4GB: initrd.img.old
  11.4GB: vmlinuz
  11.4GB: vmlinuz.old
```

How to mark a thread solved?
Reagrds

---

### Post by presence1960 on 2009-08-29
Edit the title by adding **[Solved]** at the beginning of the thread title

---

