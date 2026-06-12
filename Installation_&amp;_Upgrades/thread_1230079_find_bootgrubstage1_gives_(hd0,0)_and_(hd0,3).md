---
title: "find /boot/grub/stage1 gives (hd0,0) and (hd0,3)"
date: 2009-08-03
forum: Installation &amp; Upgrades
---

### Post by draperdt on 2009-08-03
I have a triple boot with Linux Mint 7, Windoze 7, and Fedora 11. 

Both Mint and Fedora use Grub. 

find /boot/grub/stage1 gives (hd0,0) and (hd0,3)

(hd0,0) is the Mint
(hd0,3) is the Fedora.


What I need to do: Use Mint Bootloader and it should give me option to load which ever OS I want to do.

I edited the menu.lst file in the "Mint" file system and add the corresponding entry for the Fedora. 

Now, how do I make the Fedora grub to stop and have Mint grub to display at the boot up?

I am attaching the menu.lst file for Mint. 

> 
title             Linux Mint 7 - Gloria    
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sda1 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet


title Windoze 7
root (hd0,1)
makeactive 
chainloader +1

title Linux Fedora 11
root (hd0,3)
kernel /boot/vmlinuz-2.6.29.4-167.fc11.x86_64 ro root=UUID=6605a68a-e359-4f35-a436-b2b3c65071da rhgb quiet
initrd /boot/initrd-2.6.29.4.167.fc11.x86_64.img
quiet> 


And the Menu.lst file for Fedora

[quote]
title Fedora (2.6.29.4-167.fc11.x86_64)
        root (hd0,3)
        kernel /boot/vmlinuz-2.6.29.4-167.fc11.x86_64 ro root=UUID=6605a68a-e359-4f35-a436-b2b3c65071da rhgb quiet
        initrd /boot/initrd-2.6.29.4-167.fc11.x86_64.img
title Other
        rootnoverify (hd0,1)
        chainloader +1
~                          Thanks.

---

### Post by draperdt on 2009-08-03
Update:

I rebooted the computer and I was presented with grub screen.

I set root at (hd0,0) and setup (hd0)

I now get to the Mint Bootloader. So far so good.

When I select Fedora 11 though, it says file is not found.

Hmm.

Edit: Getting a Error 15: File not found when I try to log into Fedora.

---

### Post by draperdt on 2009-08-03
I downloaded the boot info script and executed it. Below is the copy from the output. 

I am afraid to re-start the computer. 

This is where I am at. After messing around with menu.lst from both mint and fedora on my partitions, I now just want to either,

a) re-install grub and start afresh.
b) Some how fix the current issue.

I have done some research and what I have found is, in my case, I have to copy over the menu.lst of mint grub and add it to the menu.lst of Fedora.

Below is the output of the script I mentioned above.
```


============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda1 and 
                       looks at sector 40455 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Linux Mint 7 Gloria - KDE 
                       Community Edition
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda4 and 
                       looks at sector 394323274 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #4 for 
                       /boot/grub/grub.conf.
    Operating System:  Fedora release 11 (Leonidas) 
                       Kernel on an ()
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbab2bab2

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   368,627,489   368,627,427  83 Linux
/dev/sda2    *    409,593,240   476,327,249    66,734,010   7 HPFS/NTFS
/dev/sda3         476,327,250   488,392,064    12,064,815   5 Extended
/dev/sda5         476,327,313   488,392,064    12,064,752  82 Linux swap / Solaris
/dev/sda4         368,627,490   409,593,239    40,965,750  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="dabc6b47-792f-4423-803c-47923ac51d59" TYPE="ext3" 
/dev/sda2: UUID="1A7BB0440E30CF89" LABEL="Windows Partition 1" TYPE="ntfs" 
/dev/sda4: UUID="6605a68a-e359-4f35-a436-b2b3c65071da" TYPE="ext3" 
/dev/sda5: UUID="a55a683e-3b41-4f75-9dc7-fb74936baf32" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/sda4 on /mnt/Fedora type ext3 (rw)


=========================== sda1/boot/grub/menu.lst: ===========================

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
timeout          10     

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
# kopt=root=/dev/sda1 ro

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

title             Linux Mint 7 - Gloria    
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sda1 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet


title Windoze 7
root (hd0,1)
makeactive 
chainloader +1

title Linux Fedora 11
root (hd0,3)
kernel /boot/vmlinuz-2.6.29.4-167.fc11.x86_64  root=/dev/sda4 ro quiet
initrd /boot/initrd-2.6.29.4.167.fc11.x86_64.img
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=dabc6b47-792f-4423-803c-47923ac51d59 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a55a683e-3b41-4f75-9dc7-fb74936baf32 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
    .0GB: boot/initrd.img-2.6.28-11-generic
    .0GB: boot/vmlinuz-2.6.28-11-generic
    .0GB: initrd.img
    .0GB: vmlinuz

========================== sda4/boot/grub/grub.conf: ==========================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,3)
#          kernel /boot/vmlinuz-version ro root=/dev/sda4
#          initrd /boot/initrd-version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd0,3)/boot/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.29.4-167.fc11.x86_64)
    root (hd0,3)
    kernel /boot/vmlinuz-2.6.29.4-167.fc11.x86_64 ro root=UUID=6605a68a-e359-4f35-a436-b2b3c65071da rhgb quiet
    initrd /boot/initrd-2.6.29.4-167.fc11.x86_64.img
title Other
    rootnoverify (hd0,1)
    chainloader +1

=============================== sda4/etc/fstab: ===============================


#
# /etc/fstab
# Created by anaconda on Sun Aug  2 22:59:27 2009
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or vol_id(8) for more info
#
UUID=6605a68a-e359-4f35-a436-b2b3c65071da /                       ext3    defaults        1 1
UUID=a55a683e-3b41-4f75-9dc7-fb74936baf32 swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  defaults        0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0

=================== sda4: Location of files loaded by Grub: ===================


 201.8GB: boot/grub/grub.conf
 201.8GB: boot/grub/menu.lst
 201.8GB: boot/grub/stage2
 201.8GB: boot/initrd-2.6.29.4-167.fc11.x86_64.img
 201.7GB: boot/vmlinuz-2.6.29.4-167.fc11.x86_64
```
Anyone has any suggestions? :(

---

### Post by presence1960 on 2009-08-03
edit Mint's menu .lst. Edit fedora's entry to look like this:

```
title        Fedora
root         (hd0,3)
chainloader  +1
```

Chainloading is the way to go with multiple OSs. The added benefit is when each distro upgrades it's kernels each distro's menu.lst is updated only. You won't have to edit the other distro's menu.lst to include the new kernel because when you chainload it points to the other distro which has it's own update for the new kernel. The way you have it set up you would have to manually edit mint's entry for fedora each time there is a kernel upgrade

I run Jaunty, Sabayon 4.1, Mint 5 and Windows 7 RC. Jaunty's GRUB is installed to MBR of my boot drive and Mint 5 and Sabayon GRUB are installed to their partitions. Here is the OS section of my jaunty menu.lst:

> ### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista (loader)
rootnoverify	(hd0,1)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Linux Mint x64 (on /dev/sda7)
root		(hd0,6)
chainloader     +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
title		Sabayon Linux x86-64 (on /dev/sdb2)
root		(hd1,1)
chainloader     +1

---

