---
title: "Restore grub menu failed after dualbooting with XP"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by Hobbsilla on 2009-09-03
I have two questions and assuming a specific answer is given to the first it just might cancel out my second. I'm not willing to back my harddrive up and reinstall I'd rather spend hours on the internet looking up how to get it to boot again then do that. I know this community can help me get my Ubuntu partition booting again.

My first question is, if you ever need to restore or reconfigure anything using the Live CD is it best to have your Live CD be the same version of Ubuntu as the one partitioned on your computer? I'm using a live CD for Ubuntu 8.10 on my computer that has 9.04. I've attempted to restore my grub menu (menu.lst) using a number of options in the command line afterwards rebooting should restore it. However it didn't and it automatically booted into XP. I used to have a grub menu set up but had to reinstall my version of XP, i forgot to back it but was able to find it by looking at the Ubuntu partition (such a sweet feature in Linux). I edited the menu.lst file using updated options and again fail. In an effort to get the grub menu back I deleted my XP parition in hopes that it would come back and now I get this black screen that says something about no boot options. My plan is to make a Live CD with 9.04 on it but I was curious if someone could let me know if this makes a difference or not.

My second question, if the first doesn't make a difference what version of Ubuntu your Live CD is, can someone direct me to a file or a series of command line options that will make my main partition boot with the grub menu? I did the sudo grub command and configured it (did the find /boot/grub/stage1 as well) and it didn't work. I still came back to either booting into XP or after deleting XP a black screen with no boot option message.

Microsoft's competitive exclusion with their OS installation and forcing dual boot users to edit text files and grub menus would easily make a beginner to Linux less willing to give it a try.

---

### Post by presence1960 on 2009-09-03
You shouldn't just delete partitions unless you know exactly what you are doing and what the consequences of that action are. you deleted windows and the windows bootloader is on MBR and it points to your former windows partition looking for the files needed to boot, which of course no longer exist!

First, if you are going to install windows again, I would do that first before doing anything else.

After installing Windows or if you don't want windows we need to see exactly what your setup & boot process looks like.

Let's get a better look at your setup. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

> Microsoft's competitive exclusion with their OS installation and forcing dual boot users to edit text files and grub menus would easily make a beginner to Linux less willing to give it a try. You still sometimes have to edit text files and GRUB menus even when booting a second linux OS. So that statement is FALSE! That is how linux works. Are you tired of Microsoft? Then do what it takes to use Linux.

---

### Post by Hobbsilla on 2009-09-06
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda1 and 
                       looks at sector 2933063 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa635a635

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   197,711,954   197,711,892  83 Linux
/dev/sda2    *    197,724,240   228,417,839    30,693,600   7 HPFS/NTFS
/dev/sda3         228,428,235   234,436,544     6,008,310   5 Extended
/dev/sda5         228,428,298   234,436,544     6,008,247  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="6109d633-e258-42a2-a900-c55c9ae846de" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="FABC2C8ABC2C438B" TYPE="ntfs" 
/dev/sda5: UUID="7da4c4f1-34f2-46d8-91a5-14fbce4ee284" TYPE="swap" 
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# kopt=root=UUID=6109d633-e258-42a2-a900-c55c9ae846de ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=6109d633-e258-42a2-a900-c55c9ae846de ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=6109d633-e258-42a2-a900-c55c9ae846de ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.27-14-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.27-14-generic root=UUID=6109d633-e258-42a2-a900-c55c9ae846de ro quiet splash 
initrd        /boot/initrd.img-2.6.27-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.27-14-generic root=UUID=6109d633-e258-42a2-a900-c55c9ae846de ro  single
initrd        /boot/initrd.img-2.6.27-14-generic

title        Ubuntu 9.04, kernel 2.6.24-24-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=6109d633-e258-42a2-a900-c55c9ae846de ro quiet splash 
initrd        /boot/initrd.img-2.6.24-24-generic
quiet

title        Ubuntu 9.04, kernel 2.6.24-24-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=6109d633-e258-42a2-a900-c55c9ae846de ro  single
initrd        /boot/initrd.img-2.6.24-24-generic

title        Ubuntu 9.04, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows XP
root (hd0,1)
makeactive
chainloader +1

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6109d633-e258-42a2-a900-c55c9ae846de /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=7da4c4f1-34f2-46d8-91a5-14fbce4ee284 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   1.5GB: boot/grub/menu.lst
   1.5GB: boot/grub/stage2
   1.4GB: boot/initrd.img-2.6.24-24-generic
   1.1GB: boot/initrd.img-2.6.24-24-generic.bak
   1.1GB: boot/initrd.img-2.6.27-14-generic
   1.4GB: boot/initrd.img-2.6.28-15-generic
   1.2GB: boot/vmlinuz-2.6.24-24-generic
   1.3GB: boot/vmlinuz-2.6.27-14-generic
   1.1GB: boot/vmlinuz-2.6.28-15-generic
  43.5GB: grub/stage2
   1.4GB: initrd.img
   1.1GB: initrd.img.old
   1.1GB: vmlinuz
   1.3GB: vmlinuz.old

================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
```
Thanks for your help. If Ableton and Traktor Pro worked natively on Ubuntu/Linux I would abandon Windows all together. I am willing to give Windows 7 when it comes out later this year. I have a Microsoft programmer leasing my house.

---

### Post by presence1960 on 2009-09-06
I would burn a Live CD from the 9.04 iso to match the version you have installed. Boot from the Ubuntu Live CD. Choose "Try Ubuntu without any changes". When the desktop loads do this:
> 
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,0)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,0)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

**In #6 use setup (hd0)** this will put GRUB on the MBR so when you boot GRUB will take over. You installed it to the first sector of the Ubuntu partition. No good unless you are going to chainload off another bootloader!

Reboot & you will be good to go.

---

### Post by Hobbsilla on 2009-09-06
It didn't work. Do i need to edit the menu.lst file or can I edit anything on the Windows XP partition?

---

### Post by Hobbsilla on 2009-09-06
Oh oops. One setup (hd0) i accidentally had been typing hd0,0 instead. Its working now.

---

### Post by presence1960 on 2009-09-06
> **Hobbsilla said:**
> Oh oops. One setup (hd0) i accidentally had been typing hd0,0 instead. Its working now.

Glad you got it working! Enjoy Ubuntu.

---

### Post by Varox on 2009-09-08
Hi, i had to reinstall windows and im having problems putting GRUB bakc together... i tried everything i could find and nothing....

When i try to do it with the grub prompt i get this>

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 22: No such partition

And when i try to do a grub-install i get this>

Could not find device for /boot: Not found or not a block device.

Any help is welcome

---

### Post by Varox on 2009-09-08
Oh, i was forgetting smth, the results for me using the boot info script are>

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    70,573,544    70,573,482   7 HPFS/NTFS
/dev/sda2          70,573,545   234,436,544   163,863,000   5 Extended
/dev/sda5          70,573,671   228,412,169   157,838,499  83 Linux
/dev/sda3         228,412,233   234,436,544     6,024,312  82 Linux swap / Solaris

/dev/sda2 overlaps with /dev/sda3

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: TYPE="ntfs" 
/dev/sda3: TYPE="swap" UUID="0447cc4a-61b7-45a2-a22e-a75d9264eb54" 
/dev/sda5: UUID="8e48f7ca-aed8-461c-a5ce-a7903cd59318" SEC_TYPE="ext2" TYPE="ext3" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw,mode=0755)
/dev/bus/usb on /proc/bus/usb type none (rw,bind)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda5 on /mnt/system type ext3 (rw)
/dev on /mnt/system/dev type none (rw,bind)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


================================ sda1/BOOT.INI: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


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
# kopt=root=UUID=8e48f7ca-aed8-461c-a5ce-a7903cd59318 ro

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

title		Ubuntu 9.04, kernel 2.6.28-15-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=8e48f7ca-aed8-461c-a5ce-a7903cd59318 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=8e48f7ca-aed8-461c-a5ce-a7903cd59318 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=8e48f7ca-aed8-461c-a5ce-a7903cd59318 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=8e48f7ca-aed8-461c-a5ce-a7903cd59318 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=8e48f7ca-aed8-461c-a5ce-a7903cd59318 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=8e48f7ca-aed8-461c-a5ce-a7903cd59318 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-12-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=8e48f7ca-aed8-461c-a5ce-a7903cd59318 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-12-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=8e48f7ca-aed8-461c-a5ce-a7903cd59318 ro  single
initrd		/boot/initrd.img-2.6.28-12-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8e48f7ca-aed8-461c-a5ce-a7903cd59318 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8e48f7ca-aed8-461c-a5ce-a7903cd59318 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-11-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=8e48f7ca-aed8-461c-a5ce-a7903cd59318 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=8e48f7ca-aed8-461c-a5ce-a7903cd59318 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 9.04, kernel 2.6.24-21-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=8e48f7ca-aed8-461c-a5ce-a7903cd59318 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 9.04, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=8e48f7ca-aed8-461c-a5ce-a7903cd59318 ro  single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 9.04, memtest86+
root		(hd0,5)
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
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config --
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda6 :
UUID=8e48f7ca-aed8-461c-a5ce-a7903cd59318 / ext3 defaults,errors=remount-ro,relatime 0 1
# Entry for /dev/sda1 :
UUID=08AC8026AC80107C /media/sda1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda5 :
UUID=0447cc4a-61b7-45a2-a22e-a75d9264eb54 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0

=================== sda5: Location of files loaded by Grub: ===================


  76.6GB: boot/grub/menu.lst
  76.7GB: boot/grub/stage2
  76.7GB: boot/initrd.img-2.6.24-21-generic
  76.7GB: boot/initrd.img-2.6.24-21-generic.bak
  76.7GB: boot/initrd.img-2.6.27-11-generic
  76.7GB: boot/initrd.img-2.6.28-11-generic
  76.8GB: boot/initrd.img-2.6.28-12-generic
  76.7GB: boot/initrd.img-2.6.28-13-generic
  76.7GB: boot/initrd.img-2.6.28-14-generic
  76.8GB: boot/initrd.img-2.6.28-15-generic
  76.7GB: boot/vmlinuz-2.6.24-21-generic
  76.7GB: boot/vmlinuz-2.6.27-11-generic
  76.7GB: boot/vmlinuz-2.6.28-11-generic
  76.7GB: boot/vmlinuz-2.6.28-12-generic
  76.6GB: boot/vmlinuz-2.6.28-13-generic
  76.8GB: boot/vmlinuz-2.6.28-14-generic
  76.8GB: boot/vmlinuz-2.6.28-15-generic
  76.8GB: initrd.img
  76.7GB: initrd.img.old
  76.8GB: vmlinuz
  76.8GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb

---

### Post by presence1960 on 2009-09-08
Your Ubuntu entries in menu.lst are all out of order and have the wrong root (hdx,y) designation. They all have root (hd0,5) - your ubuntu is sda5 which is (hd0,4). So the first thing you need to do is boot from the Live CD. Choose "try Ubuntu without any changes". Open a file browser and click on the Ubuntu partition on the left pane. Once it is mounted open a terminal and run this command ```
gksu nautilus
```.
On the left pane click on the partition that has Ubuntu installed and then navigate to the /boot/grub/menu.lst file. Double click to open menu.lst. Change all the root (hd0,5) entries in each kernel to root (hd0,4). be careful as you are root. Do not edit anything other than the root (hd0,5) entries. When completed click Save on the toolbar and close the file. You can close both file browsers also. 

Now you want to restore GRUB. pick up at #2 below

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,4)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,4)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

**In #6 use setup (hd0)**
```

Reboot & you should be good to go.

---

### Post by presence1960 on 2009-09-08
I just noticed your /etc/fstab output. Your Ubuntu partition was originally sda6 and swap was originally sda5. You did more than just install windows, you changed your partition table also. That is why your menu.lst has root (hd0,5) instead of root (hd0,4).

Hopefully the above will work since fstab identifies partitions/devices by UUID.

---

