---
title: "GRUB problems"
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by Until It Sleeps on 2009-02-24
I recently installed Windows 7 onto a logical partition. It deleted GRUB. I ran a Ubuntu CD, started a terminal, did the commands from that little tutorial that tells you how to restore GRUB.

Now, GRUB is back, but now it's not detecting Windows 7, and I'm not entirely sure how the solution on the tutorial is supposed to be used. Little help please? Thanks.

---

### Post by caljohnsmith on 2009-02-24
In order to get a clearer picture of your setup, how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and what it might take to boot Windows 7 from Grub.

---

### Post by Until It Sleeps on 2009-02-24
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa7e2a7e2

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    78,140,159    78,140,097  83 Linux
/dev/sda2          78,140,160    80,100,089     1,959,930   5 Extended
/dev/sda5          78,140,223    80,100,089     1,959,867  82 Linux swap / Solaris
/dev/sda3    *     80,101,376    80,510,975       409,600   7 HPFS/NTFS
/dev/sda4          80,510,976   117,207,039    36,696,064   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="c956d815-3573-4e1f-b7b2-4ead7dd50d1d" TYPE="ext3" 
/dev/sda3: UUID="3EE8B72BE8B6E077" TYPE="ntfs" 
/dev/sda4: UUID="5CC0B1C2C0B1A2A6" TYPE="ntfs" 
/dev/sda5: UUID="3b1374f5-4dd8-4e54-9ce9-53cd1369fdf9" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/untilitsleeps/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=untilitsleeps)


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
default saved

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
# kopt=root=UUID=c956d815-3573-4e1f-b7b2-4ead7dd50d1d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c956d815-3573-4e1f-b7b2-4ead7dd50d1d

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
uuid		c956d815-3573-4e1f-b7b2-4ead7dd50d1d
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=c956d815-3573-4e1f-b7b2-4ead7dd50d1d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		c956d815-3573-4e1f-b7b2-4ead7dd50d1d
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=c956d815-3573-4e1f-b7b2-4ead7dd50d1d ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		c956d815-3573-4e1f-b7b2-4ead7dd50d1d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c956d815-3573-4e1f-b7b2-4ead7dd50d1d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		c956d815-3573-4e1f-b7b2-4ead7dd50d1d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c956d815-3573-4e1f-b7b2-4ead7dd50d1d ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		c956d815-3573-4e1f-b7b2-4ead7dd50d1d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c956d815-3573-4e1f-b7b2-4ead7dd50d1d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=3b1374f5-4dd8-4e54-9ce9-53cd1369fdf9 none            swap    sw              0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  11.1GB: boot/grub/menu.lst
  11.1GB: boot/grub/stage2
  11.1GB: boot/initrd.img-2.6.27-11-generic
  11.1GB: boot/initrd.img-2.6.27-7-generic
  11.1GB: boot/vmlinuz-2.6.27-11-generic
  11.1GB: boot/vmlinuz-2.6.27-7-generic
  11.1GB: initrd.img
  11.1GB: initrd.img.old
  11.1GB: vmlinuz
  11.1GB: vmlinuz.old
```

---

### Post by caljohnsmith on 2009-02-24
Actually, it looks like you installed Windows 7 to primary partition sda4, but Windows 7's boot files ended up in sda3. How about first opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And at the very bottom add:
```
title Windows 7
root (hd0,2)
chainloader +1
```
Reboot, try Windows 7 from your Grub menu, and let me know exactly what happens. We can work from there if necessary.

---

### Post by Until It Sleeps on 2009-02-25
Hey thanks, it worked! 

I do have to press Esc to get to the menu, but it lists Windows 7, and it does load it. Thanks for the help.

---

### Post by caljohnsmith on 2009-02-25
Great, glad to hear that worked OK. And by the way, if you want to get the Grub menu on start up by default without having to press "ESC", just comment-out the "hiddenmenu" line in your menu.lst:
```
[COLOR="Blue"]#[/COLOR] hiddenmenu
```
Anyway, cheers and enjoy your dual-boot Win7/Ubuntu setup. :)

---

