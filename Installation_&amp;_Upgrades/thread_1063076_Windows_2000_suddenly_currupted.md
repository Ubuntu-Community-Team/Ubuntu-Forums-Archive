---
title: "Windows 2000 suddenly currupted?"
date: 2009-02-07
forum: Installation &amp; Upgrades
---

### Post by dwjenkins on 2009-02-07
I have a recent and very frustrating problem that has popped up in my dual boot system. One element has been Windows 2000 Server as a constant for two or three years now and nothing has changed there, and the other element is the latest version of Ubuntu. Suddenly, I'm not exactly sure at what point recently, when I tried to boot Windows 2000 via Grub, I got a BSOD with the message: "***STOP: 0X0000007B (0XF681B848, 0C000000E, 0X00000000, 0X00000000) INACCESSIBLE_BOOT_DEVICE" and a lot of advice about checking for viruses and new hard drives and checking the drive for curruption, etc. I've been through the process of reinstalling Windows which will boot just fine by itself, and then reinstalling Ubuntu Intrepid and Hardy and even Linux Mint which I guess is based on Ubuntu, but I get the same results when Ubuntu installs the boot loader and tries to boot, the above message. The Windows boot process actually starts with its splash screen, so I think Grub is directing things to the right place, and it reads right (HD0,0). But I'm wondering if somehow the installation of Ubuntu corrupts Windows. When I go back to the Windows installer, it invariably shows the first partition it was supposed to be in as damaged or "unknown." Has anyone else run into Ubuntu doing this kind of thing?

Thanks,
Don J.

---

### Post by caljohnsmith on 2009-02-07
I think it would help to get more info about your setup, so how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by dwjenkins on 2009-02-07
I did as you asked, and the results were interesting in one regard:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x69205244

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   168,648,479   168,648,417   7 HPFS/NTFS
/dev/sda2         168,650,370   291,113,864   122,463,495  83 Linux
/dev/sda3         291,113,865   299,146,364     8,032,500  82 Linux swap / Solaris
/dev/sda4         299,146,365   488,392,064   189,245,700  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="480C0C200C0C0C1E" TYPE="ntfs" 
/dev/sda2: UUID="b572f87c-486f-408d-8233-cb9352afcd7b" TYPE="ext3" 
/dev/sda3: TYPE="swap" UUID="75dfa48e-5cfd-4043-b21f-c988eb469eae" 
/dev/sda4: UUID="e6ec2843-dba8-4c63-8e2d-3def9d544b70" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
/dev/sda4 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)

================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINNT
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows 2000 Server" /fastdetect

=========================== sda2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=b572f87c-486f-408d-8233-cb9352afcd7b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=b572f87c-486f-408d-8233-cb9352afcd7b ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=b572f87c-486f-408d-8233-cb9352afcd7b ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows 2000 Server
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=b572f87c-486f-408d-8233-cb9352afcd7b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=e6ec2843-dba8-4c63-8e2d-3def9d544b70 /home           ext3    relatime        0       2
# /dev/sda3
UUID=75dfa48e-5cfd-4043-b21f-c988eb469eae none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


 138.3GB: boot/grub/menu.lst
 138.3GB: boot/grub/stage2
 138.2GB: boot/initrd.img-2.6.24-16-generic
 138.1GB: boot/initrd.img-2.6.24-16-generic.bak
 138.1GB: boot/vmlinuz-2.6.24-16-generic
 138.2GB: initrd.img
 138.1GB: vmlinuz

=======Devices which don't seem to have a corresponding hard drive==============

 sdb .


```

At the very first where Grub identifies SDa1, it identifies the boot sector as Windows XP, which it is not. The rest of the way through, however, it seems to be correctly identified as 2000. I'm not sure where Grub is doing this identification or how to change it if it is the problem. Anything else out of order?

Thanks,
Don J.

---

### Post by caljohnsmith on 2009-02-07
It's OK that the script identifies the sda1 boot sector as Windows XP, because both Windows XP and Windows 2000 use the same boot sector, i.e. they both try to boot the Windows "ntldr" file. Your sda1 partition mounted and read just fine, so at least it's not corrupted in that sense. Also, since your Windows entry in Grub's menu.lst is correct, I think you have a Windows problem and not a Grub problem at this point. If you want to prove whether that is true or not, you could temporarily replace Grub in the MBR with a Windows MBR, and that should allow you to boot directly into Windows if Windows is indeed OK. You can do that by booting your Windows Install CD, go to the recovery console, and run:
```
fixmbr
```
Then reboot your HDD and see if you can boot into Windows OK (I think you will have the same problem, but I could be wrong). When you are ready to get Grub back, just boot your Live CD, open a terminal and do:
```
sudo grub
grub> root (hd0,1)
grub> setup (hd0)
grub> quit

```
Good luck and let me know how it goes.

---

### Post by dwjenkins on 2009-02-07
Did it. Grub is fine. Windows is broken. I can only surmise that somehow the process of installing Ubuntu after installing Windows breaks it for some mysterious reason that is recent. I was always able to set up my system in that order in the past without this kind of problem. Windows always boots fine right after I install it. It only comes up broken after I go on to install Ubuntu and try to boot it from Grub. I may try another distro or two to verify. Right now everything is hosed and waiting to be rebuilt, anyway. Like I said, I've never had this kind of problem with the two before. The only other thing that might be possible is that I did change to a larger SATA hard drive a little while back, which is where everything is residing. I could take that off line and try my old IDE HD and see if that makes a difference. 

Thanks for your help,
Don J.

---

### Post by dwjenkins on 2009-02-08
When I tried installing Windows 2000 yet again, and the installation files would not even load properly, I decided to take the SATA HD off line and put my old IDE HD back on and try that. It solved the problems completely, so it seems to have been an intermittently failing HD that just wasn't going to work with Windows. Linux seems to be more forgiving longer with these HD errors. I'll either go with my old drive, which is adequate, but slower, or go pick up a new SATA drive Monday. 

Thanks for your help,
Don J.

---

### Post by caljohnsmith on 2009-02-08
I know that XP (which is similar to Win 2000) requires special SATA drivers to install to a SATA drive, or if you can set your SATA drive to use "IDE-legacy" mode or similar in your BIOS, that usually works. I would imagine that Windows 2000 is similar to XP in that regard, so are you doing anything special when trying to install Win 2000 to your SATA drive? Maybe that's the issue. Before you conclude the HDD is failing, I would run some HDD diagnostic tests on it; did you get any on a CD that came with that HDD? If not, you can usually download diagnostic software from the HDDs manufacturer's website, or download something like the [Ultimate Boot CD]("http://www.ultimatebootcd.com") and use the HDD tests that some with it. Good luck and let me know what you come up with.

---

### Post by dwjenkins on 2009-02-09
I downloaded the UBCD and did the quick and long tests and found no errors on my SATA drive, so it does not seem to be a problem that way. I then used the UBCD to wipe it clean just so Windows wouldn't be confused this time. Then I checked around in my Bios and found where to change to the Legacy mode for Win 2000 and did that. I installed Windows again, and it went fine and a lot faster than before and booted up fine afterwards like it was supposed to. But then when I Installed Linux and that installed Grub and I went back to boot Windows, by then Windows had been corrupted somewhere along the line by the Linux install. I'm wondering if the partitioner does something. I always do a manual install, but I never touch the NTFS partition. I don't know, though, it seems to be disc specific, because it didn't happen with the older IDE hard drive. I'm always putting Windows in the first partition. I didn't get a disc with the drive. 

Don J.

---

### Post by caljohnsmith on 2009-02-09
How about reinstalling Windows again, confirm it boots after installing it, then boot your Live CD, open gparted (System > Admin > Partition Editor), use gparted to resize your Windows partition, and then reboot to make sure Windows still boots OK. If it does, how about using gparted again to manually set up your Ubuntu and swap partitions (and any other partitions you might want), then reboot again to make sure Windows is still OK. If Windows is OK, then how about trying to install Ubuntu again using the "manual" partition option, but this time you won't need to set up any partitions; just set the mount point of your main Ubuntu partition to "/" and the swap partition as "swap". Please make sure you do not set a mount point on the Windows partition or mark it any way when you are in the installer (leave it entirely untouched). Also please don't change any of the settings under the "Advanced" button near the end of the installation process. If you can try that, I think it will work, and if not, at least we will have a better idea of where in the process your Windows partition is getting "corrupted." Let me know how that goes.

---

### Post by dwjenkins on 2009-02-09
I wanted to do some variant of the above, but I was having problems with the partitioner showing the disc as "unusable" after creating one partition in supposedly total free space. So I ran the UBCD and used a wiping program to do a total wipe, one pass with random stuff and one for zeros, which took hours. But when it was done I started over with Windows, then Ubuntu, and everything seems to be booting as it should. Maybe there was some bad info secreted somewhere that kept popping up that finally got gone. I'll see as I try to switch back and forth to get all the drivers installed to make W2000 functional again now. How nice that Ubuntu at least comes that way. Meanwhile, I am keeping all your notes for "in case." 

Thanks,
Don J.

---

