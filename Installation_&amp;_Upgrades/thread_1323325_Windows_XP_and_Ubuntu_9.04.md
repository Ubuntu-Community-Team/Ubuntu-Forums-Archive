---
title: "Windows XP and Ubuntu 9.04"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by jackpotmoney on 2009-11-11
Hi,

I installed Ubuntu 9.04 on my desktop. I installed the same thing on my laptop as well.

On my laptop, I was able to get Ubuntu 9.04 working just fine and I could get into Windows Vista just fine.


On my desktop, I was able to install Ubuntu 9.04 and it works just fine, except that it is running out of memory and I know how to fix that, but the thing I could not work is the Windows XP.

There are 2 other operating system that it says is on my computer.
I click  on one of the  windows xp OS. 

One of them starts up into a black screen and says "Starting up" and then it does nothing.
The other one starts up and it starts up computer recovery.


So how do I boot up windows XP?

---

### Post by coffeecat on 2009-11-11
> **jackpotmoney said:**
> On my desktop, I was able to install Ubuntu 9.04 and it works just fine, except that it is running out of memory and I know how to fix that, but the thing I could not work is the Windows XP.

There are 2 other operating system that it says is on my computer.
I click  on one of the  windows xp OS. 

One of them starts up into a black screen and says "Starting up" and then it does nothing.
The other one starts up and it starts up computer recovery.


So how do I boot up windows XP?

There are two entries in Grub because the Ubuntu installer found two NTFS partitions with a Windows bootloader. Except that one is your manufacturer's recovery partition, as you have discovered. This is quite common. I got two Windows grub entries on my Sony laptop when I installed 9.04, but both had the same title. I suppose the grub installer can't tell the difference and falls back onto a generic title.

Anyway, the grub menu item you want is the one that at the moment is taking you to a black screen, which is Windows trying to start up, except it can't because clearly something has gone wrong with Windows.

Try this: select the menu entry that takes you to a black screen. **Immediately**, press the F8 key and hold it. Hopefully, this will take you to a white on black menu that offers you safe mode, a repair option and a couple of other options. Try safe mode first. If that works, reboot and see if it will now boot up into the regular desktop. If it doesn't, try holding F8 again and try the repair option. I don't know what's in there because I've never used it, but hopefully there will be something to get you going again.

---

### Post by jackpotmoney on 2009-11-11
> **coffeecat said:**
> There are two entries in Grub because the Ubuntu installer found two NTFS partitions with a Windows bootloader. Except that one is your manufacturer's recovery partition, as you have discovered. This is quite common. I got two Windows grub entries on my Sony laptop when I installed 9.04, but both had the same title. I suppose the grub installer can't tell the difference and falls back onto a generic title.

Anyway, the grub menu item you want is the one that at the moment is taking you to a black screen, which is Windows trying to start up, except it can't because clearly something has gone wrong with Windows.

Try this: select the menu entry that takes you to a black screen. **Immediately**, press the F8 key and hold it. Hopefully, this will take you to a white on black menu that offers you safe mode, a repair option and a couple of other options. Try safe mode first. If that works, reboot and see if it will now boot up into the regular desktop. If it doesn't, try holding F8 again and try the repair option. I don't know what's in there because I've never used it, but hopefully there will be something to get you going again.

That didn't do anything.

I held on it for a couple of minutes and nothing happened. 

It just still said "Starting up".

---

### Post by raymondh on 2009-11-11
A friend (presence1960+) would say  .....

"Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text."    :)

I may not have presence1960's analytical skills but I can give this my best effort ;)

Boot info script in my signature below, as well.

---

### Post by jackpotmoney on 2009-11-11
> **raymondhenson said:**
> A friend (presence1960+) would say  .....

"Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command

```
sudo bash ~/Desktop/boot_info_script*.sh
```This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text."    :)

I may not have presence1960's analytical skills but I can give this my best effort ;)

Boot info script in my signature below, as well.

It won't download.
I can't update ubuntu without enough memory. So thats why I am trying to get into windows to edit the partition.

And it won't download

---

### Post by raymondh on 2009-11-11
> **jackpotmoney said:**
> It won't download.
I can't update ubuntu without enough memory. So thats why I am trying to get into windows to edit the partition.

And it won't download

Try using the liveCD of 9.04 and get to a live session (TRY UBUNTU WITHOUT ANY CHANGES).  Once in live session, access the web to download and save to desktop.  Run the terminal (applications > accessories)  command and it'll save the results.txt to desktop.  Access the web again and this forum/thread and paste back the results.txt file.

Using a live session and saving to its' desktop is OK.  It'll only be deleted/erased once you exit live session.

PS.  Will be back in 30 minutes ... dinner time for the kids.

---

### Post by jackpotmoney on 2009-11-11
> **raymondhenson said:**
> Try using the liveCD of 9.04 and get to a live session (TRY UBUNTU WITHOUT ANY CHANGES).  Once in live session, access the web to download and save to desktop.  Run the terminal (applications > accessories)  command and it'll save the results.txt to desktop.  Access the web again and this forum/thread and paste back the results.txt file.

Using a live session and saving to its' desktop is OK.  It'll only be deleted/erased once you exit live session.

PS.  Will be back in 30 minutes ... dinner time for the kids.
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcab10bee

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   284,125,589   284,125,527   7 HPFS/NTFS
/dev/sda2         294,613,200   312,575,759    17,962,560   c W95 FAT32 (LBA)
/dev/sda3         284,125,590   294,599,969    10,474,380   5 Extended
/dev/sda5         289,362,843   294,262,604     4,899,762  83 Linux
/dev/sda6         294,262,668   294,599,969       337,302  82 Linux swap / Solaris
/dev/sda7         284,125,716   289,009,349     4,883,634  83 Linux
/dev/sda8         289,009,413   289,362,779       353,367  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="58D017C5D017A7F0" LABEL="PRESARIO" TYPE="ntfs" 
/dev/sda2: LABEL="PRESARIO_RP" UUID="4B6E-6BC0" TYPE="vfat" 
/dev/sda5: UUID="93a021c5-a6fa-4922-aee3-409f893639a3" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="6f339492-8633-445a-a439-23354a22d158" TYPE="swap" 
/dev/sda7: UUID="6e8d87a0-9ffa-42a7-848a-41a6bee55b64" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: UUID="4a804f5e-b78f-43d7-b1cf-6d832b576122" TYPE="swap" 
/dev/ramzswap0: TYPE="swap" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect 

================================ sda2/boot.ini: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

================================ sda2/BOOT.INI: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

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
# kopt=root=UUID=93a021c5-a6fa-4922-aee3-409f893639a3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=93a021c5-a6fa-4922-aee3-409f893639a3

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        93a021c5-a6fa-4922-aee3-409f893639a3
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=93a021c5-a6fa-4922-aee3-409f893639a3 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        93a021c5-a6fa-4922-aee3-409f893639a3
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=93a021c5-a6fa-4922-aee3-409f893639a3 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        93a021c5-a6fa-4922-aee3-409f893639a3
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows XP Media Center Edition
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows NT/2000/XP
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1


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
UUID=93a021c5-a6fa-4922-aee3-409f893639a3 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=6f339492-8633-445a-a439-23354a22d158 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 149.7GB: boot/grub/menu.lst
 149.7GB: boot/grub/stage2
 149.7GB: boot/initrd.img-2.6.28-11-generic
 149.7GB: boot/vmlinuz-2.6.28-11-generic
 149.7GB: initrd.img
 149.7GB: vmlinuz

=========================== sda7/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=6e8d87a0-9ffa-42a7-848a-41a6bee55b64 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6e8d87a0-9ffa-42a7-848a-41a6bee55b64

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        6e8d87a0-9ffa-42a7-848a-41a6bee55b64
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=6e8d87a0-9ffa-42a7-848a-41a6bee55b64 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        6e8d87a0-9ffa-42a7-848a-41a6bee55b64
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=6e8d87a0-9ffa-42a7-848a-41a6bee55b64 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        6e8d87a0-9ffa-42a7-848a-41a6bee55b64
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows XP Media Center Edition
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows NT/2000/XP
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=93a021c5-a6fa-4922-aee3-409f893639a3 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=93a021c5-a6fa-4922-aee3-409f893639a3 ro single 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 9.04, memtest86+ (on /dev/sda5)
root        (hd0,4)
kernel        /boot/memtest86+.bin  
savedefault
boot


=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=6e8d87a0-9ffa-42a7-848a-41a6bee55b64 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=4a804f5e-b78f-43d7-b1cf-6d832b576122 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 146.7GB: boot/grub/menu.lst
 146.7GB: boot/grub/stage2
 147.4GB: boot/initrd.img-2.6.28-11-generic
 146.0GB: boot/vmlinuz-2.6.28-11-generic
 147.4GB: initrd.img
 146.0GB: vmlinuz

```

---

### Post by raymondh on 2009-11-11
chainload entry/ies for both media center and recovery look ok.

When you access XP and it hangs on "starting" .... are there any more errors stated.  I ask because this tells me that GRUB is working ok and passing on the bootloading job to windows' bootloader.  I think the problem is in the windows bootloader .... though I am not definite hence my question regarding "any more error messages".

Another question ... do you have an original windows XP install disc (not the recovery disc supplied by HP) ?  If my hunch is right, we will have to (in order)

-  Fix the boot sector (fixboot or fixmbr) of windows > which will require using the xp install disc.
- Re-install GRUB from the 9.04 liveCD as the previous fixboot/fixmbr will erase GRUB

Lastly, you do know you have 2 9.04 installs, right?

Regards,

---

### Post by jackpotmoney on 2009-11-11
> **raymondhenson said:**
> chainload entry/ies for both media center and recovery look ok.

When you access XP and it hangs on "starting" .... are there any more errors stated.  I ask because this tells me that GRUB is working ok and passing on the bootloading job to windows' bootloader.  I think the problem is in the windows bootloader .... though I am not definite hence my question regarding "any more error messages".

Another question ... do you have an original windows XP install disc (not the recovery disc supplied by HP) ?  If my hunch is right, we will have to (in order)

-  Fix the boot sector (fixboot or fixmbr) of windows > which will require using the xp install disc.
- Re-install GRUB from the 9.04 liveCD as the previous fixboot/fixmbr will erase GRUB

Lastly, you do know you have 2 9.04 installs, right?

Regards,

There are no other thing after when it says "Starting up"
I don't have another windows xp start up cd.

I also don't want to lose my files. I didn't import the bookmarks from my original browser I was using on firefox. And i have alot of files that are very important.

And I dont know that I have two ubuntus.

---

### Post by raymondh on 2009-11-11
> **jackpotmoney said:**
> There are no other thing after when it says "Starting up"
I don't have another windows xp start up cd.

I also don't want to lose my files. I didn't import the bookmarks from my original browser I was using on firefox. And i have alot of files that are very important.

And I dont know that I have two ubuntus.

[http://www.supergrubdisk.org/index.php?pid=5](http://www.supergrubdisk.org/index.php?pid=5)

Above link is for super grub disk.  Read through its' documentation and see if it'll suit your needs.  You can use that to access XP.

If you think that the MBR is corrupted and decide to fix it using supergrub disk, the action (in super grub disk) is english > advanced > windows > fix mbr or fix boot.  Note that this will overwrite GRUB which you will have to re-install using the 9.04 liveCD.

Here's a [reference from Herman's webpage]("http://members.iinet.net.au/%7Eherman546/p15.html#disk_IO_error").

And to [re-install GRUB]("http://ubuntuforums.org/showthread.php?t=224351").

Another workaround to this is to completely recover your XP install using the built-in recovery feature ..... updating XP ... erasing the Ubuntu install and expanding the existing XP partition ... defragging XP ...... and re-doing the ubuntu install. 

If you wish, you can wait for another poster/forum member to chime in.

Nevertheless, have a working back-up of your files saved elsewhere.  If you haven't, you can use the liveCD and go live session.  Look in PLACES for your files and copy/save them to a USB drive or external drive.

We can work on the 2nd ubuntu install after you get to recover XP completely.

---

### Post by jackpotmoney on 2009-11-11
> **raymondhenson said:**
> [http://www.supergrubdisk.org/index.php?pid=5](http://www.supergrubdisk.org/index.php?pid=5)

Above link is for super grub disk.  Read through its' documentation and see if it'll suit your needs.  You can use that to access XP.

If you think that the MBR is corrupted and decide to fix it using supergrub disk, the action (in super grub disk) is english > advanced > windows > fix mbr or fix boot.  Note that this will overwrite GRUB which you will have to re-install using the 9.04 liveCD.

Here's a [reference from Herman's webpage]("http://members.iinet.net.au/%7Eherman546/p15.html#disk_IO_error").

And to [re-install GRUB]("http://ubuntuforums.org/showthread.php?t=224351").

Another workaround to this is to completely recover your XP install using the built-in recovery feature ..... updating XP ... erasing the Ubuntu install and expanding the existing XP partition ... defragging XP ...... and re-doing the ubuntu install. 

If you wish, you can wait for another poster/forum member to chime in.

Nevertheless, have a working back-up of your files saved elsewhere.  If you haven't, you can use the liveCD and go live session.  Look in PLACES for your files and copy/save them to a USB drive or external drive.

We can work on the 2nd ubuntu install after you get to recover XP completely.


Is there a simpler way to go back into windows Xp than that?

I found a windows xp professional service pack 3 for my Dell computer.

Will that work to fix it?

---

### Post by raymondh on 2009-11-11
> **jackpotmoney said:**
> Is there a simpler way to go back into windows Xp than that?

I found a windows xp professional service pack 3 for my Dell computer.

Will that work to fix it?

we need an install disc to access the repair function and a command prompt. The command prompt is like the terminal (it is) in linux.  Is it a install disc with SP3?

That or redoing the whole install thru your built-in recovery.  That however will take gobs of time.

Have you backed-up/saved your files?

---

### Post by jackpotmoney on 2009-11-11
> **raymondhenson said:**
> we need an install disc to access the repair function and a command prompt. The command prompt is like the terminal (it is) in linux.  Is it a install disc with SP3?

That or redoing the whole install thru your built-in recovery.  That however will take gobs of time.

Have you backed-up/saved your files?

Yes its an install disc.


And I cant back up my files, I have no USB or external harddrive.

---

### Post by raymondh on 2009-11-11
just thought of something .....

a couple of weeks ago, I was helping a friend who had an acer netbook that had a pre-installed recovery partition.  He had installed Ubuntu but messed up.  What happened was that he could not access his XP.  Grub was only showing the recovery partition.  Likewise, he did not have a install disc.  What we ended up doing (after saving his files elsewhere) was

-  Boot into the liveCD (9.04) and access gparted.
-  Made sure swap was set to swapoff
-  Deleted the ubuntu and swap install (as well as the extended partition) leaving an unallocated space
-  Re-installed ubuntu (manual) which also reinstalled GRUB

We had no problems after that.  What got me thinking was that maybe it would've been simpler to just re-install GRUB.  But my friend wanted a separate /home as well hence the full re-install of Ubuntu.

We could try to re-install GRUB right now and see if it will connect your XP.  If not, then I am more assured that XP's bootloader in the MBR is corrupt thus requiring a fixMBR.

---

### Post by jackpotmoney on 2009-11-11
> **raymondhenson said:**
> just thought of something .....

a couple of weeks ago, I was helping a friend who had an acer netbook that had a pre-installed recovery partition.  He had installed Ubuntu but messed up.  What happened was that he could not access his XP.  Grub was only showing the recovery partition.  Likewise, he did not have a install disc.  What we ended up doing (after saving his files elsewhere) was

-  Boot into the liveCD (9.04) and access gparted.
-  Made sure swap was set to swapoff
-  Deleted the ubuntu and swap install (as well as the extended partition) leaving an unallocated space
-  Re-installed ubuntu (manual) which also reinstalled GRUB

We had no problems after that.  What got me thinking was that maybe it would've been simpler to just re-install GRUB.  But my friend wanted a separate /home as well hence the full re-install of Ubuntu.

We could try to re-install GRUB right now and see if it will connect your XP.  If not, then I am more assured that XP's bootloader in the MBR is corrupt thus requiring a fixMBR.

ok ill try that tomorrow.
I got to go and finish up on some things.

Thanks!

---

### Post by raymondh on 2009-11-11
> **jackpotmoney said:**
> Yes its an install disc.


**And I cant back up my files, I have no USB or external harddrive.**

Then a recovery partition re-install will not work as it will erase everything.

Your decision :

1.  Reinstall GRUB to see if it works or,
2.  Go ahead and fixMBR to access XP and then re-install GRUB to access Ubuntu

---

### Post by efflandt on 2009-11-11
When you first got your HP computer did it come with any CD's or data DVD's, or did you create (burn) The HP Recovery Tools CD and DVD (or a bunch of CD's)?

The HP Recovery Tools CD should be able to boot and if you select Recovery Console, it can reboot into that.  From there you could run **fixmbr** which would restore the master boot record.  But I don't know if that would correct your Windows problem, and then you would need the install CD to boot Ubuntu until grub was reinstalled.

It would have been nice to have had the output of **sudo fdisk -l** from before you did anything.  On my older HP desktop, the recovery partition was first and then the XP partition.  I wonder if something rearranged the partitions or changed the disk geometry from when it was originally partitioned.

When I installed WinXP 64 beta, it changed geometry of my 200 G drive from 240 heads to 255 heads and different cylinders, and XP 64 beta could not even boot itself, much less 32-bit XP Home.  It took me awhile to reconstruct the partition table from (biological) memory (my head).  SuSE Linux installation was going to do the same thing until I stopped it and told it to use an existing partition.  Although, your geometry is normal for a 160 G drive (my 160 G laptop or USB Passport show up as 255 heads, 63 sectors/track, 19457 cylinders).

From **Places** in Ubuntu can you get into HP_PAVILION (or whatever it calls your HP ntfs partition)?  See what boot.ini shows for Windows boot location.  If it shows multi(0)disk(0)rdisk(0)partition(2) it may need to be changed to multi(0)disk(0)rdisk(0)partition(1), because that is where your Windows is now.  Although, if you have to edit that file I would do it on a Windows PC to make sure that line endings are correct. DOS/Win use carriage return/linefeed (\r\n), while Linux just uses linefeed (also known as newline or \n).

Following are hints for for shrinking a Windows partition to make room for Linux:  Back up anything you do not want to lose (copy to CD or DVD if nothing else).  Disable virtual memory in Windows (which normally reserves unmovable file space), then reboot.  Defrag Windows to move all files to the bottom of the drive.  Re-enable virtual memory after the Windows partition has been shrunk.

---

### Post by raymondh on 2009-11-11
> **efflandt said:**
> When you first got your HP computer did it come with any CD's or data DVD's, or did you create (burn) The HP Recovery Tools CD and DVD (or a bunch of CD's)?

The HP Recovery Tools CD should be able to boot and if you select Recovery Console, it can reboot into that.  From there you could run **fixmbr** which would restore the master boot record.  But I don't know if that would correct your Windows problem, and then you would need the install CD to boot Ubuntu until grub was reinstalled.

It would have been nice to have had the output of **sudo fdisk -l** from before you did anything.  On my older HP desktop, the recovery partition was first and then the XP partition.  I wonder if something rearranged the partitions or changed the disk geometry from when it was originally partitioned.
.

Thanks for the assist efflandt.  The fisk -l output is in the boot info script (1st page).  Maybe you could spot something I missed.

Regards,

---

### Post by presence1960 on 2009-11-11
you can use testdisk from ubuntu to rebuild your windows MBR, then restore GRUB to MBR.

If not installed already install testdisk by running in terminal ```
sudo apt-get install testdisk
```

Start testdisk by running in terminal ```
sudo testdisk
``` You will get a message about testdisk needing more space in terminal- just enlarge terminal by dragging bottom right corner with mouse.

Choose No Log
Select disk with windows on it
At partition table type select Intel
Select windows partition and choose Rebuild BS on bottom.

When you reboot if your Windows boot sector is repaired you will boot right into windows and have to restore GRUB.
---------------------------------------------------------------------------------------------------------------------

Or if you can get any windows XP install disk you can fix windows by booting off the disk and doing this:

For this you will need your Windows XP installation CD. Boot into it now.

You will get to a part where it asks if you want to repair or recover. To do so, press "r".

If prompted, enter your Windows XP administrator password. This will leave you at at a command line, so type in the following two commands:

```

fixboot
```

&

```
fixmbr
```

Then type

```
exit
```

Reboot & remove disk if you boot right into windows then you can restore GRUB to MBR

---

