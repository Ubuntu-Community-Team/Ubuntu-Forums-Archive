---
title: "Installed Ubuntu 8.10 on Acer Aspire One, now Windows Won't Boot"
date: 2009-03-02
forum: Installation &amp; Upgrades
---

### Post by k1dicarus on 2009-03-02
Hello everyone!

I just installed Intrepid on a new Acer Aspire One ZG5 alongside the existing Windows XP installation on the machine. Relatively painless install, except for the fact that when I tried to restart the computer into Windows, after selecting it through grub, I am greeted by an infinitely blinking cursor instead. I still have access to my Windows partition on the computer through Ubuntu, just need Windows for some things, too!
Anyone have any ideas on how I can boot back into XP??

Thanks so much!

..I forgot to mention.. I don't have an external CD drive at the moment..

---

### Post by deepclutch on 2009-03-02
do you have Linux and windows on seperate harddisks?and Linux is installed on the booting harddisk?

---

### Post by caljohnsmith on 2009-03-02
If you can boot into your Ubuntu install, how about doing that, download the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your Windows booting problem might be.

---

### Post by k1dicarus on 2009-03-02
Okay, here are the results of that script:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

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

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x11a8ba38

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    10,236,050    10,235,988  12 Compaq diagnostics
/dev/sda2    *     10,236,051   185,244,709   175,008,659   7 HPFS/NTFS
/dev/sda3         185,245,515   312,576,704   127,331,190   5 Extended
/dev/sda5         185,245,578   307,291,319   122,045,742  83 Linux
/dev/sda6         307,291,383   312,576,704     5,285,322  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="PQSERVICE" UUID="0159-6699" TYPE="vfat" 
/dev/sda2: UUID="589408A7F001C7B1" LABEL="ACER" TYPE="ntfs" 
/dev/sda5: UUID="93b52a05-8548-4150-86d8-8273d450e5aa" TYPE="ext3" 
/dev/sda6: UUID="f72c9bae-410d-429a-a0c3-eb6369bdf0bd" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/david/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=david)


================================ sda2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


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
# kopt=root=UUID=93b52a05-8548-4150-86d8-8273d450e5aa ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=93b52a05-8548-4150-86d8-8273d450e5aa

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

title		Ubuntu 8.10, kernel 2.6.28sickboy-kuki
uuid		93b52a05-8548-4150-86d8-8273d450e5aa
kernel		/boot/vmlinuz-2.6.28sickboy-kuki root=UUID=93b52a05-8548-4150-86d8-8273d450e5aa ro quiet splash 
initrd		/boot/initrd.img-2.6.28sickboy-kuki
quiet

title		Ubuntu 8.10, kernel 2.6.28sickboy-kuki (recovery mode)
uuid		93b52a05-8548-4150-86d8-8273d450e5aa
kernel		/boot/vmlinuz-2.6.28sickboy-kuki root=UUID=93b52a05-8548-4150-86d8-8273d450e5aa ro  single
initrd		/boot/initrd.img-2.6.28sickboy-kuki

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		93b52a05-8548-4150-86d8-8273d450e5aa
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=93b52a05-8548-4150-86d8-8273d450e5aa ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, memtest86+
uuid		93b52a05-8548-4150-86d8-8273d450e5aa
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=93b52a05-8548-4150-86d8-8273d450e5aa /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=f72c9bae-410d-429a-a0c3-eb6369bdf0bd none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 153.6GB: boot/grub/menu.lst
 153.6GB: boot/grub/stage2
 153.5GB: boot/initrd.img-2.6.27-11-generic
 153.5GB: boot/initrd.img-2.6.27-12-generic
 153.5GB: boot/initrd.img-2.6.27-7-generic
 153.5GB: boot/initrd.img-2.6.28sickboy-kuki
 153.5GB: boot/vmlinuz-2.6.27-11-generic
 153.5GB: boot/vmlinuz-2.6.27-12-generic
 153.5GB: boot/vmlinuz-2.6.27-7-generic
 153.5GB: boot/vmlinuz-2.6.28sickboy-kuki
 153.5GB: initrd.img
 153.5GB: initrd.img.old
 153.5GB: vmlinuz
 153.5GB: vmlinuz.old
```

Also, this was happening before I applied the kuki kernel..

Thanks again for your help!

---

### Post by caljohnsmith on 2009-03-02
OK, how about opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And then delete the following Windows entry near the end of the file:
```
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
chainloader	+1

```
Then reboot, and try the "Microsoft Windows XP Home Edition" entry in your Grub menu, and let me know what happens. We can work from there.

---

### Post by k1dicarus on 2009-03-02
Alright, just tried that, and it's still giving me the cursor. :-k

---

### Post by k1dicarus on 2009-03-02
It will be great when we get this figured out. I could imagine this happening to quite a few people. I can't wait for Karmic! :D

---

### Post by caljohnsmith on 2009-03-02
It sounds like your Windows partition boot sector may need fixing, so how about first making sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk /dev/sda2
```
After starting testdisk, choose "Proceed", "None", "Advanced", "Boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "Extrapolated boot sector and current boot sector are different", then choose "Write". After you are done doing the "Rebuild BS" in testdisk, reboot and let me know exactly what happens when you boot Windows XP from the Grub menu. Or if testdisk says the boot sectors are identical and doesn't give you an option to "Rebuild BS", let me know, and we can work from there.

---

### Post by k1dicarus on 2009-03-02
Alright, the attached screenshot is what I get when it's done rebuilding.

When I tried to reboot into XP, in the top left it read Starting up..., then underneath it there was an odd strain of symbols (hearts and stuff) and a blinking cursor after those.

---

### Post by caljohnsmith on 2009-03-02
OK, how about booting your Windows Install CD, press "r" at the first main menu to go to the "recovery console", and then do:
```
map
```
That will show the drive letters for your partitions; find the drive letter for the Windows partition (for example "C") and do:
```
chkdsk /r C:
```
And run chkdsk as many times as it takes until it reports no errors. Then try booting Windows again and let me know what happens.

---

### Post by k1dicarus on 2009-03-02
Unfortunately, I don't have an external CD drive for this netbook. I do have an XP install disc, though.. is there any other method we could try?

---

### Post by k1dicarus on 2009-03-04
Okay, I guess I'll just get an external CD drive.

---

