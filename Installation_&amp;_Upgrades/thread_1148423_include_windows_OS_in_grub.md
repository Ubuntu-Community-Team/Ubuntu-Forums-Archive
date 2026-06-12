---
title: "include windows OS in grub"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by solitaire on 2009-05-04
Hi
I'm trying to get a triple boot laptop.

I originally  had a dual boot Laptop. I've shrunk the windows Vista partition and installed Win7 in the blank area. I've recovered the original Grub so i can boot in to Ubuntu or Vista. 

What do i need to add into menu.lst so that i can boot to the win7 OS?

---

### Post by caljohnsmith on 2009-05-04
It would help to get info about your setup before we can offer specific advice for how to boot Windows 7, so how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

John

---

### Post by solitaire on 2009-05-04
Thanks for the reply

I've copied the results.txt to this post.

*NOTE*

sda1: Vista partiton (can boot into this)

sda2: Win7 partition

sda4: Is the HP Recovery Partition

sdb1: is a SD card


```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Acer 3 is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

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

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x80d2f3ee

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    97,659,134    97,659,072   7 HPFS/NTFS
/dev/sda2          97,660,928   195,317,759    97,656,832   7 HPFS/NTFS
/dev/sda3         195,318,270   293,700,329    98,382,060   5 Extended
/dev/sda5         195,318,333   291,756,464    96,438,132  83 Linux
/dev/sda6         291,756,528   293,700,329     1,943,802  82 Linux swap / Solaris
/dev/sda4         293,703,344   312,581,807    18,878,464   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2032 MB, 2032664576 bytes
32 heads, 40 sectors/track, 3101 cylinders, total 3970048 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d484f

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     3,970,047     3,969,985  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="0515A45E72386AE3" TYPE="ntfs" 
/dev/sda2: UUID="1A7E012F7E0104EB" TYPE="ntfs" 
/dev/sda4: UUID="485221BD5221B09C" LABEL="HP_RECOVERY" TYPE="ntfs" 
/dev/sda5: UUID="1e2a2a2a-fd27-4126-ade2-47843141890d" TYPE="ext3" 
/dev/sda6: UUID="a917600c-95ed-4d8b-a7a7-1af45ab6e729" TYPE="swap" 
/dev/sdb1: UUID="b62bf7e1-9ca1-4d7b-bfad-97185ccb493d" TYPE="ext4" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/bill/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bill)
/dev/sdb1 on /media/disk type ext4 (rw,nosuid,nodev,uhelper=hal)


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
# kopt=root=UUID=1e2a2a2a-fd27-4126-ade2-47843141890d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1e2a2a2a-fd27-4126-ade2-47843141890d

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
uuid        1e2a2a2a-fd27-4126-ade2-47843141890d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=1e2a2a2a-fd27-4126-ade2-47843141890d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        1e2a2a2a-fd27-4126-ade2-47843141890d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=1e2a2a2a-fd27-4126-ade2-47843141890d ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.27-14-generic
uuid        1e2a2a2a-fd27-4126-ade2-47843141890d
kernel        /boot/vmlinuz-2.6.27-14-generic root=UUID=1e2a2a2a-fd27-4126-ade2-47843141890d ro quiet splash 
initrd        /boot/initrd.img-2.6.27-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode)
uuid        1e2a2a2a-fd27-4126-ade2-47843141890d
kernel        /boot/vmlinuz-2.6.27-14-generic root=UUID=1e2a2a2a-fd27-4126-ade2-47843141890d ro  single
initrd        /boot/initrd.img-2.6.27-14-generic

title        Ubuntu 9.04, memtest86+
uuid        1e2a2a2a-fd27-4126-ade2-47843141890d
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (Home Basic)
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        HP Boot'n'Nuke
root        (hd0,1)
savedefault
makeactive
chainloader    +1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=1e2a2a2a-fd27-4126-ade2-47843141890d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=a917600c-95ed-4d8b-a7a7-1af45ab6e729 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 124.3GB: boot/grub/menu.lst
 120.8GB: boot/grub/stage2
 120.8GB: boot/initrd.img-2.6.27-14-generic
 120.8GB: boot/initrd.img-2.6.28-11-generic
 127.0GB: boot/vmlinuz-2.6.27-14-generic
 120.8GB: boot/vmlinuz-2.6.28-11-generic
 120.8GB: initrd.img
 120.8GB: initrd.img.old
 120.8GB: vmlinuz
 127.0GB: vmlinuz.old

```

---

### Post by caljohnsmith on 2009-05-04
The Boot Info Script confirms what I suspected, namely that Windows 7 put its boot files in your Vista partition; that's the usual way Windows sets up a dual-boot between two Windows OSes. To boot Vista and Windows 7 separately from your Grub menu, I would recommend following [meierfra's excellent tutorial]("http://ubuntuforums.org/showthread.php?t=1146266"). Let me know how that goes or if you run into any problems.

John

---

### Post by solitaire on 2009-05-04
Thanks
I'll take a look and try it out later in the week.

Since Win7 RC is out for public download in a few hours I'll wait till I've installed that to sort the Boot out.

---

### Post by solitaire on 2009-05-08
I Installed "Win7 RC"

I repaired Grub.

Looks like The Windows Boot manager Pops up after i select the windows option in Grubs menu..

So everything it OK. Thanks for your help..

---

