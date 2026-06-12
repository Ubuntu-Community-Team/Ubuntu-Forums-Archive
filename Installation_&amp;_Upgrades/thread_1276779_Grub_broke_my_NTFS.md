---
title: "Grub broke my NTFS"
date: 2009-09-27
forum: Installation &amp; Upgrades
---

### Post by sysst on 2009-09-27
Hello

I have 2 hard drives, and I was dual booting Windows and Linux.
Today I decided to mess with Grub to move it from the second drive to the first, and I applied some commands inside grub, one of them is : root (...) and another is setup (...)
Now the system is still bootable as it was, but one of my partitions, NTFS, became inaccessible.
Windows tells me that it's not formated, and Linux shows it on the left hand menus (places), but not inside the folder media, I guess because it's not mounted, and it seems I can't mount it also, and when I click it, it takes me to the root folder.
Also it is showing with (ext4) sign, but I didn't format anything! and when i make fdisk -l. it shows that it's NTFS.
The partition had some data, are they lost?

Thanks in advance. Please ask me if you think I should give more information.

---

### Post by stlsaint on 2009-09-27
please post the outcome of fdisk -l and post your menu.lst....          ```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by sysst on 2009-09-27
> **stlsaint said:**
> please post the outcome of fdisk -l and post your menu.lst....          ```
gksudo gedit /boot/grub/menu.lst
```

Here is menu.lst:

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0

## Graphical boot menu location
gfxmenu=/boot/gfxmenu/linuxmint.message

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

# Pretty colours
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
# kopt=root=/dev/sdb3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,2)

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
##      altoptions=(single-user) single
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

title        Linux Mint 7 Gloria KDE, kernel 2.6.28-11-generic
root        (hd1,2)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sdb3 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Linux Mint 7 Gloria KDE, kernel 2.6.28-11-generic (recovery mode)
root        (hd1,2)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sdb3 ro single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Linux Mint 7 Gloria KDE, memtest86+
root        (hd1,2)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1






And this is fdisk-l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc0fb34e1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2845    22852431    7  HPFS/NTFS
/dev/sda2            2846        9729    55295730    f  W95 Ext'd (LBA)
/dev/sda5            2846        9729    55295698+   7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d19bb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12158    97659103+   7  HPFS/NTFS
/dev/sdb2           12159       12280      979965   82  Linux swap / Solaris
/dev/sdb3           12281       14593    18579172+  83  Linux



The lost partition is sda5 which is a logical partition of the extended partition sda2


Thanks for the reply

---

### Post by presence1960 on 2009-09-27
Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by tuxxy on 2009-09-27
You could also use Super Grub Disk.

---

### Post by sysst on 2009-09-27
> **presence1960 said:**
> Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

I also would like to mention something, I'm not running Ubuntu itself, it's Linux mint on KDE, but I suppose it's the same in this situation.
And one more thing, this has a little tool for removable disks, and I just noticed that it's showing this partition down there beside the clock as removable, together with my external HD, and when I try to remove it, it says cannot unmount, one or more files are open, and when I open it, it take me to the root folder, which I'm starting to guess because I applied the root (hd...) something inside grub??


```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /grldr /ntldr 
                       /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda2 and 
                       looks at sector 197392888 on boot drive #2 for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #3 for 
                       /boot/grub/menu.lst.

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda5 and 
                       looks at sector 197392888 on boot drive #2 for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #3 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdb3 and 
                       looks at sector 197392888 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #3 for 
                       /boot/grub/menu.lst.
    Operating System:  Linux Mint 7 Gloria - KDE 
                       Community Edition
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc0fb34e1

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    45,704,924    45,704,862   7 HPFS/NTFS
/dev/sda2          45,704,925   156,296,384   110,591,460   f W95 Ext d (LBA)
/dev/sda5          45,704,988   156,296,384   110,591,397   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d19bb

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   195,318,269   195,318,207   7 HPFS/NTFS
/dev/sdb2         195,318,270   197,278,199     1,959,930  82 Linux swap / Solaris
/dev/sdb3         197,278,200   234,436,544    37,158,345  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="80F46D6CF46D657E" LABEL="System" TYPE="ntfs" 
/dev/sdb1: UUID="4E386132386119EB" LABEL="Passport" TYPE="ntfs" 
/dev/sdb2: TYPE="swap" UUID="c583b426-8514-47fe-8004-9c298a112d9b" 
/dev/sdb3: UUID="71940d12-441f-4d3c-86b0-fc85c06096ec" TYPE="ext4" 

=============================== "mount" output: ===============================

/dev/sdb3 on / type ext4 (rw,relatime,errors=remount-ro)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sda1 on /media/System type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /media/Passport type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=3
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional" /FASTDETECT /NoExecute=OptIn

=========================== sdb3/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0

## Graphical boot menu location
gfxmenu=/boot/gfxmenu/linuxmint.message

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

# Pretty colours
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
# kopt=root=/dev/sdb3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,2)

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
##      altoptions=(single-user) single
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

title        Linux Mint 7 Gloria KDE, kernel 2.6.28-11-generic
root        (hd1,2)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sdb3 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Linux Mint 7 Gloria KDE, kernel 2.6.28-11-generic (recovery mode)
root        (hd1,2)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sdb3 ro single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Linux Mint 7 Gloria KDE, memtest86+
root        (hd1,2)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb3 during installation
UUID=71940d12-441f-4d3c-86b0-fc85c06096ec /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb2 during installation
UUID=c583b426-8514-47fe-8004-9c298a112d9b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb3: Location of files loaded by Grub: ===================


 116.2GB: boot/grub/menu.lst
 101.0GB: boot/grub/stage2
 103.6GB: boot/initrd.img-2.6.28-11-generic
 103.5GB: boot/initrd.img-2.6.28-11-generic.mybackup
 116.1GB: boot/vmlinuz-2.6.28-11-generic
 103.6GB: initrd.img
 116.1GB: vmlinuz

```

Thanks

---

### Post by presence1960 on 2009-09-27
you really have a mess there! You have a windows XP bootloader with a windows Vista bootsector type and you have both XP's and vista's files needed to boot on sda1. Your menu.lst entry for windows says Vista. Which version of windows are you using?

You also installed GRUB to sda2 & sda5 the extended partitions. I would try to recover the data there before doing anything else. If you can't mount sda5 from the Mint Live Cd try burning a backtrack Linux CD & boot from that. Get Backtrack Linux [here]("http://www.remote-exploit.org/backtrack.html").

After you save your data if possible post back & we'll start working on the rest. You don't want to use sda as you may render your data unrecoverable. Boot from the backtrack CD and see if you can recover your data from sda5 and move it to another location.

---

### Post by sysst on 2009-09-27
> **presence1960 said:**
> you really have a mess there! You have a windows XP bootloader with a windows Vista bootsector type and you have both XP's and vista's files needed to boot on sda1. Your menu.lst entry for windows says Vista. Which version of windows are you using?

You also installed GRUB to sda2 & sda5 the extended partitions. I would try to recover the data there before doing anything else. If you can't mount sda5 from the Mint Live Cd try burning a backtrack Linux CD & boot from that. Get Backtrack Linux [here]("http://www.remote-exploit.org/backtrack.html").

After you save your data if possible post back & we'll start working on the rest. You don't want to use sda as you may render your data unrecoverable. Boot from the backtrack CD and see if you can recover your data from sda5 and move it to another location.

OK i'll try that.

Now to explain what happened more:
I have sda as a fixed drive, with two partition, first one has XP and second has Vista, and the Vista boot loader was taking care of them.

sdb is an external HD, it was all ntfs but I made an ext4 (sdb3) for Linux.
And when I installed Linux on it, it put grub on the external HD, which caused a problem when I remove the external drive, I cannot go to windows at all. I wanted to put grub on the fixed hd, sda.
It seems I applied tooo many setup(hda,...) which put it everywhere, luckily not on the active partition, otherwise I would have lost XP too, now I lost the vista partition (sda5) only.

So is the problem that grub cannot be installed on an ntfs partition? or why did it make the partition format raw, as XP now tells me when I try chkdsk to fix the ntfs?

And is there any way to fix the partition MFT (Master File Table)
I'll be trying this also:
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

Let's see

---

### Post by presence1960 on 2009-09-27
Unplug your external disk & you need to repair Vista by doing this:

To restore the Windows Vista bootloader, you must first boot off your Windows Vista installation DVD.
When you get to the Regional settings, select your Location/Keyboard setting then click next. On the next page you must click on "Repair your computer."

On the next page, if it finds your Windows Vista installation, make sure it is UNSELECTED before clicking next.
Then click on "Command prompt". From there, type in the folowing:

```
bootrec.exe /fixboot
```

```
bootrec.exe /fixmbr
```

Now close the two windows and click "Restart."

This will repair Vista and put Vista on MBR of your internal disk. When you reboot keep your external unplugged and see if you boot into windows. report back then we can put GRUB on MBR of your external disk, provided your machine is capable of booting from a removable disk / USB

---

### Post by sysst on 2009-09-27
> **presence1960 said:**
> Unplug your external disk & you need to repair Vista by doing this:

To restore the Windows Vista bootloader, you must first boot off your Windows Vista installation DVD.
When you get to the Regional settings, select your Location/Keyboard setting then click next. On the next page you must click on "Repair your computer."

On the next page, if it finds your Windows Vista installation, make sure it is UNSELECTED before clicking next.
Then click on "Command prompt". From there, type in the folowing:

```
bootrec.exe /fixboot
``````
bootrec.exe /fixmbr
```Now close the two windows and click "Restart."

This will repair Vista and put Vista on MBR of your internal disk. When you reboot keep your external unplugged and see if you boot into windows. report back then we can put GRUB on MBR of your external disk, provided your machine is capable of booting from a removable disk / USB

I have eayBCD on XP, should I try using it to write the vista boot loader?
Note that doing this will make me unable to go to Linux again until I reinstall grub.

---

### Post by presence1960 on 2009-09-27
> **sysst said:**
> I have eayBCD on XP, should I try using it to write the vista boot loader?
Note that doing this will make me unable to go to Linux again until I reinstall grub.
I know very little about Easy BCD. I find that GRUB can take care of booting multiple OSs in varying file system formats with ease.

That is your call. If you want to use Easy BCD I suggest you wait for someone who knows about it to come along. But you will still have to repair Vista because installing GRUB on the Vista partition (sda5) is why you can not mount Vista.

---

### Post by sysst on 2009-09-27
> **sysst said:**
> 
And is there any way to fix the partition MFT (Master File Table)
I'll be trying this also:
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

Let's see


Wow it worked!

This program is awesome, I downloaded TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
As described, it has an option to "Recover NTFS boot sector from its backup"
The symptoms they described are exactly what I had, and it took one second, and the partition opened again, now it's time to clean the mess I made with grub.

I still have the same configuration but now luckily my data are safe, is there a safe why to put grub on the fixed disk?

Thanks for all the trouble (edit) I meant all the trouble that i caused :)

---

### Post by stlsaint on 2009-09-27
put grub on the fixed hdd the same way you put it on the other drives

Boot to livecd

```
enter terminal then type sudo grub
```

```
find /boot/grub/stage1
```
"it will give you something like (hd0,1) just for example"
take whatever it gives you and use with next cmd so....
```
Root (hd0,1)
```
yes you need the paranthesis

```
Setup (hd0)
``` 
this will put Grub on the MBR of your hdd of selection, if you want to put it to a specific partition you would use (hd0,1) but in your case i it seems you want it to MBR.

Grub should tell you it was successful then reboot and you should see your OS's.
We may have to edit your menu.lst some so post back when done.

---

### Post by sysst on 2009-09-28
> **stlsaint said:**
> put grub on the fixed hdd the same way you put it on the other drives

Boot to livecd

```
enter terminal then type sudo grub
``````
find /boot/grub/stage1
```"it will give you something like (hd0,1) just for example"
take whatever it gives you and use with next cmd so....
```
Root (hd0,1)
```yes you need the paranthesis

```
Setup (hd0)
```this will put Grub on the MBR of your hdd of selection, if you want to put it to a specific partition you would use (hd0,1) but in your case i it seems you want it to MBR.

Grub should tell you it was successful then reboot and you should see your OS's.
We may have to edit your menu.lst some so post back when done.

Thanks I did just that and the original problem remained, which is as I understand now, unsolvable.
The problem is that menu.lst is in the Linux partition on the external drive, so the external drive always has to be plugged no matter where Grub is installed.

However now I have another issue, it seems installing Grub on hd0 made both Windows OSes unbootable, although strangely the Vista boot menu still appears. But selecting Vista or XP gives a missing file error. Mint is still bootable though.
I'm gonna restore Vista boot loader and try something other than Grub which always required files in the Linux parition (menu.lst, ?)

Any suggestions? 
I'll need a boot loader that doesn't rely on any file on a non-ntfs partition, so it won't have to access the external drive containing Linux except if it wants to boot Linux itself.

Cheers.

Edit: I added my menu.lst
```

## ## End Default Options ##

title        Linux Mint 7 Gloria KDE, kernel 2.6.28-11-generic
root        (hd1,2)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sdb3 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Linux Mint 7 Gloria KDE, kernel 2.6.28-11-generic (recovery mode)
root        (hd1,2)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sdb3 ro single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Linux Mint 7 Gloria KDE, memtest86+
root        (hd1,2)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1
```

---

### Post by presence1960 on 2009-09-28
Is your machine capable of booting from USB? If so put GRUB on MBR of USB and restore Windows to MBR of internal disk. Then set the USB to boot before the hard disk (internal). If you have the USB disk unplugged windows will boot, if you have the USB plugged in GRUB will boot and you can boot into Ubuntu. If you need help setting it up post back.

---

### Post by sysst on 2009-09-28
> **presence1960 said:**
> Is your machine capable of booting from USB? If so put GRUB on MBR of USB and restore Windows to MBR of internal disk. Then set the USB to boot before the hard disk (internal). If you have the USB disk unplugged windows will boot, if you have the USB plugged in GRUB will boot and you can boot into Ubuntu. If you need help setting it up post back.

This is a very good idea and it worked well.
To explain the steps:
First in Linux, install grub on the external drive mbr
Shutdown, remove the external drive.
Repair vista boot loader
Set Bios to boot from the external drive as first boot device, and from fixed HD as second.

Thank you

---

### Post by presence1960 on 2009-09-28
Glad you got it working! Enjoy Ubuntu.

---

