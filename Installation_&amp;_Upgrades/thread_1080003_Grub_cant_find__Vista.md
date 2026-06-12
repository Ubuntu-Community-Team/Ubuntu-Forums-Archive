---
title: "Grub cant find  Vista"
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by Vrekk on 2009-02-24
Hey I installed 8.10 recentaly, but grub didnt find Vista for my dual boot.  Can someone help me out here?  I am not the only person who uses this computer and they need Vista.

---

### Post by frost151n on 2009-02-25
Can you post the out put of

```
sudo gedit /boot/grub/menu.lst
```

It'll show what your Visa entry looks like.

---

### Post by caljohnsmith on 2009-02-25
In order to get a clearer picture of your setup, how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and what it might take to boot Vista from Grub.

---

### Post by Vrekk on 2009-02-25
Here
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /BOOT/bcd /Windows/System32/winload.exe

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7d8c7d8c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     2,104,514     2,104,452  82 Linux swap / Solaris
/dev/sda2          10,120,950   976,751,999   966,631,050   f W95 Ext d (LBA)
/dev/sda5         488,119,023   976,751,999   488,632,977   7 HPFS/NTFS
/dev/sda6          10,121,076   475,973,819   465,852,744  83 Linux
/dev/sda7         475,973,883   488,118,959    12,145,077  82 Linux swap / Solaris
/dev/sda3           2,104,515    10,120,949     8,016,435  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="8f2e69c4-bc45-4343-83d0-fb847ef35a41" TYPE="swap" 
/dev/sda3: UUID="506fb74e-fb38-4418-aaf1-c04fd0eb16e5" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="7CD8A472D8A42BF8" TYPE="ntfs" 
/dev/sda6: UUID="d89990a7-2081-49ad-b5d5-b02b8f2604a1" TYPE="ext3" 
/dev/sda7: UUID="a3d52c7e-4aca-413b-82e0-bdc30393de91" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/brett/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=brett)
/dev/scd0 on /media/2007.11.03_2329 type udf (ro,nosuid,nodev,uhelper=hal,uid=1000)


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
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=d89990a7-2081-49ad-b5d5-b02b8f2604a1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d89990a7-2081-49ad-b5d5-b02b8f2604a1

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		d89990a7-2081-49ad-b5d5-b02b8f2604a1
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=d89990a7-2081-49ad-b5d5-b02b8f2604a1 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		d89990a7-2081-49ad-b5d5-b02b8f2604a1
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=d89990a7-2081-49ad-b5d5-b02b8f2604a1 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		d89990a7-2081-49ad-b5d5-b02b8f2604a1
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d89990a7-2081-49ad-b5d5-b02b8f2604a1 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		d89990a7-2081-49ad-b5d5-b02b8f2604a1
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d89990a7-2081-49ad-b5d5-b02b8f2604a1 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		d89990a7-2081-49ad-b5d5-b02b8f2604a1
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Vista
rootnoverify (hd0,4)
chainloader +1

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=d89990a7-2081-49ad-b5d5-b02b8f2604a1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=a3d52c7e-4aca-413b-82e0-bdc30393de91 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 220.3GB: boot/grub/menu.lst
 220.2GB: boot/grub/stage2
 220.3GB: boot/initrd.img-2.6.27-11-generic
 220.2GB: boot/initrd.img-2.6.27-7-generic
 220.2GB: boot/vmlinuz-2.6.27-11-generic
 220.2GB: boot/vmlinuz-2.6.27-7-generic
 220.3GB: initrd.img
 220.2GB: initrd.img.old
 220.2GB: vmlinuz
 220.2GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by caljohnsmith on 2009-02-25
Part of the issue is you have Vista installed to sda5, which is a logical partition; booting Windows from a logical partition usually takes special steps, because normally Windows can only boot from a primary partition. The other issue is that your Vista sda5 partition has a Windows XP boot sector, i.e. the boot sector is configured to boot XP's "ntldr" rather than Vista's "bootmgr". To fix the Vista boot sector, how about booting your Vista Install CD, go to the command line and do:
```
bootrec /fixboot
```
If you don't have your Vista Install CD handy, you can instead download and use a Vista Recovery CD from either of these sources:

[http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/](http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/)
[http://www.pcworld.com/downloads/file/fid,71039/description.html](http://www.pcworld.com/downloads/file/fid,71039/description.html)

Your current Vista entry in Grub's menu.lst should work to boot Vista, so once you've fixed Vista's boot sector, try booting Vista from your Grub menu and let me know exactly what happens. We can work from there if necessary.

---

### Post by Vrekk on 2009-02-25
Nothing Happens when I run that code.  I get an Invaid Filesystem error or something along though lines.  Then I tried
```
bootrec /fixmbr
```
to see if I could boot into Vista (Yes i know i disabled Grub).  But Vista still didnt work

Any other ideas? (Yes I but Grub back in the MBR)

---

### Post by caljohnsmith on 2009-02-25
OK, how about downloading the attached "Vista_PBR_9sectors.txt" file to your desktop and do:
```
sudo dd if=~/Desktop/Vista_PBR_9sectors.txt of=/dev/sda5 bs=80 skip=1 seek=1 conv=notrunc
```
Then try booting Vista from your Grub menu and let me know exactly what happens, especially if you get any type of Vista errors.

---

### Post by Vrekk on 2009-02-25
Not really sure what you had me do, but it works now.  I can select vista from the list and it boots.  Seemed to be a little bit slower, but i dont care, I wont be using it much.

Thanks

BTW what did that code do?

---

### Post by caljohnsmith on 2009-02-25
> **Vrekk said:**
> 
BTW what did that code do?
It's a special virus code that will cause Vista to self-destruct after approximately 3 more reboots. :shock: Just kidding, what we did was manually install a Vista boot sector to your Vista partition. Anyway, glad that worked OK; cheers and have fun with Ubuntu and Vista. :)

---

