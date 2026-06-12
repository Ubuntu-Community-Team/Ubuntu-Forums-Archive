---
title: "Win7 + Ubuntu Jaunty"
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by Shedgaladh on 2009-10-23
Hi there,

i have a problem with dual booting my system, i hope this is the right forum for this topic. Basically, i had Windows 7 installed on my computer and then i wanted to switch to Ubuntu at first. I decided want to have both: Windows 7 and Ubuntu.

The problem i have is very difficult for me. I try to explain what i did until now. At first i tried to install ubuntu to /sda/sda4 and installing GRUB normally. I ended up with missing Win7 boot (of cause, grub was installed to the previous win7 loader) but that was the smallest problem.Great Problem was:

grub loading stage 1.5
please wait
Grub Error 21

i checked this forum and other forums and tried to find help in alredy answered topics, nothing helped. i learned, he can't find the disc probably cause of the jni sata-controller i got.

i searched for other options and found wubi.installed it, it startet and denn the grub loader worked. It found the wubi installation AND my own installed Ubuntu installation. So i uninstalled wubi ... normal grub should find my installation also ... but nothing.

I ended up trying to follow this:

[http://www.iceflatline.com/2009/09/how-to-dual-boot-windows-7-and-linux-using-bcdedit/comment-page-1/]("http://www.iceflatline.com/2009/09/how-to-dual-boot-windows-7-and-linux-using-bcdedit/comment-page-1/")

So, i'm here now:

when the computer boots the windows boot loader starts, i can choose between Win7 and Ubuntu. Win7 starts normally but Ubuntu does not. I get an grub> console, nothing more. i tried find (hd<TAB> and got error 15 file not found.

Anyone got a idea?

Shedy

I'm sorry for my bad english, hope you can understand me.

---

### Post by presence1960 on 2009-10-23
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Shedgaladh on 2009-10-24
Thanks for the quick reply:

hier is the content of the RESULTS.TXT

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     Grub0.97 in the file /linux.bin looks at sector 
                       329710458 of the same hard drive for the stage2 file. 
                       A stage2 file is at this location on /dev/sda. Stage2 
                       looks on partition #4 for /boot/grub/menu.lst.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

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
                       looks at sector 329710458 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #4 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Platte /dev/sda: 250.0 GByte, 250059350016 Byte
255 Köpfe, 63 Sektoren/Spuren, 30401 Zylinder, zusammen 488397168 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Disk identifier: 0x689fafb6

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   328,650,751   328,443,904   7 HPFS/NTFS
/dev/sda3         480,472,020   488,392,064     7,920,045   5 Extended
/dev/sda5         480,488,085   488,392,064     7,903,980  82 Linux swap / Solaris
/dev/sda4         328,657,770   480,472,019   151,814,250  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="4AE0F37AE0F36B19" LABEL="System Reserved" TYPE="ntfs" 
/dev/sda2: UUID="66D8420CD841DAC7" TYPE="ntfs" 
/dev/sda4: UUID="e86a9faf-bff8-45fd-bf48-6937174046d9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="2622c2e6-65b7-46d5-be11-276750413f72" 

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


=========================== sda4/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=e86a9faf-bff8-45fd-bf48-6937174046d9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e86a9faf-bff8-45fd-bf48-6937174046d9

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
uuid        e86a9faf-bff8-45fd-bf48-6937174046d9
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e86a9faf-bff8-45fd-bf48-6937174046d9 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        e86a9faf-bff8-45fd-bf48-6937174046d9
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e86a9faf-bff8-45fd-bf48-6937174046d9 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        e86a9faf-bff8-45fd-bf48-6937174046d9
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
chainloader    +1


=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda4 during installation
UUID=e86a9faf-bff8-45fd-bf48-6937174046d9 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=2622c2e6-65b7-46d5-be11-276750413f72 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda4: Location of files loaded by Grub: ===================


 168.8GB: boot/grub/menu.lst
 168.8GB: boot/grub/stage2
 168.8GB: boot/initrd.img-2.6.28-11-generic
 168.9GB: boot/vmlinuz-2.6.28-11-generic
 168.8GB: initrd.img
 168.9GB: vmlinuz
```

---

### Post by presence1960 on 2009-10-24
You have GRUB installed on Vista's partition and on Ubuntu's partition. You need to put GRUB on MBR so GRUB will come up at boot.

There may be another complication - if you look at the output here from the script you are missing some Vista boot files (in red). If Vista boots fine then don't worry about it.

```
sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     Grub0.97 in the file /linux.bin looks at sector 
                       329710458 of the same hard drive for the stage2 file. 
                       A stage2 file is at this location on /dev/sda. Stage2 
                       looks on partition #4 for /boot/grub/menu.lst.
    Operating System:  Windows Vista
    [COLOR="Red"]Boot files/dirs:   /Windows/System32/winload.exe[/COLOR]

```

To put GRUB on MBR do this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,3)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,3)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

```

Now you need to add Vista to the GRUB menu. Boot into Ubuntu and open a terminal. Run this command ```
gksu gedit /boot/grub/menu.lst
```

scroll down to this spot near the bottom:

**### END DEBIAN AUTOMAGIC KERNELS LIST**

skip one line then add these entries:

```
 This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows Vista 
rootnoverify    (hd0,1)
chainloader     +1

 This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Vista Recovery
rootnoverify    (hd0,0)
chainloader     +1
```

Click Save on the toolbar & close the file. Reboot and try your OSs.

---

### Post by Shedgaladh on 2009-10-24
Thanks again but it will not work.

i tried installing Grub to mbr in first place, it gave me the error with loading stage 1.5 error 21 i mentioned before. i will not be able to boot at all unless from live cd.
thats why i wanted to install grub loader into the boot loader from windows 7.

i wonder what wubi does to install itself to the windows 7 boatloader cause basically thats what i'am trying to achieve with the difference that i want to install Ubuntu from another partition than the windows partition.

any suggestions? :(

edit says:

the biggest problem why i can't use Grub as bootloader in first place is that my hd  doesn't show up in BIOS. It's handle with the jmicron sata controller. so that was the reason why i wanted to use win7 boot loader.

another idea, when i want to boot ubuntu i get a grub> console. Can i somehow try to boot ubuntu from here on?

---

### Post by Shedgaladh on 2009-10-24
Problem solved.

Thank you again presence1960 for trying to help me.

The solution was very easy but in another way than i thougth.
The problem really WAS the jmicron controller, so the only thing i had to do is ... plug the cable of the hd in another slot ...

now the disk shows up in bios and i can boot ubtuntu *cheer*

Shed

---

### Post by presence1960 on 2009-10-24
> **Shedgaladh said:**
> Problem solved.

Thank you again presence1960 for trying to help me.

The solution was very easy but in another way than i thougth.
The problem really WAS the jmicron controller, so the only thing i had to do is ... plug the cable of the hd in another slot ...

now the disk shows up in bios and i can boot ubtuntu *cheer*

Shed

Glad you got it working! Enjoy Ubuntu.

---

