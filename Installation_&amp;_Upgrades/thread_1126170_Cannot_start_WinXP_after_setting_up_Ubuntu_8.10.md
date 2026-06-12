---
title: "Cannot start WinXP after setting up Ubuntu 8.10"
date: 2009-04-15
forum: Installation &amp; Upgrades
---

### Post by nguyenthetam on 2009-04-15
I am new to Ubuntu and need some help.

I have 1 hard disk (150 GB). When setting up Windows XP I partitioned it into 3 partitions (20G, 80G and 50G).

Then I setup WinXP on the first partition. Windows has been working well since then. Yesterday I just installed Ubuntu 8.10 on the third partition and now I can only start Ubuntu but cannot start WinXP. The system says: [COLOR="Red"]**HAL.dll is corrupted or missing !!!**[/COLOR] I can use Ubuntu to see content of 'Windows partition'. Everything is still there  !

How can I do now ? Thanks ...

Here is my GRUB' menu:
[COLOR="Blue"]
title		Ubuntu 8.10, kernel 2.6.27-7-generic
root (hd0,2)
uuid		41d43c1c-e145-439e-a4b2-0dd6f5143d44
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=41d43c1c-e145-439e-a4b2-0dd6f5143d44 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet
...

title		Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1
[/COLOR]

Here is fdisk's info:

[COLOR="Blue"]Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x23262325

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        2611    20964825    f  W95 Ext'd (LBA)
/dev/sda2            2612       12810    81923467+   7  HPFS/NTFS
/dev/sda3   *       12811       18889    48829567+  83  Linux
/dev/sda4           18890       19457     4562460   82  Linux swap / Solaris
/dev/sda5   *           2        2611    20964793+   7  HPFS/NTFS[/COLOR]

And the attachment is partition info

---

### Post by Bucky Ball on 2009-04-15
Try:

[COLOR=Blue]title        Windows XP Professional
root        (hd0,**0**)
savedefault
makeactive
chainloader    +1

Change to (hd0,0).

At the grub menu screen, choose the windows install and press 'e' to edit. Try it out in there to see if it works before changing anything permanently.

There are instructions for getting around the edit screen at the bottom of the screen.
[/COLOR]

---

### Post by nguyenthetam on 2009-04-15
> **Bucky Ball said:**
> Try:

[COLOR=Blue]title        Windows XP Professional
root        _(hd0,**0**)_
savedefault
makeactive
chainloader    +1

Change to (hd0,0).

At the grub menu screen, choose the windows install and press 'e' to edit. Try it out in there to see if it works before changing anything permanently.

There are instructions for getting around the edit screen at the bottom of the screen.
[/COLOR]

I tried to change it to (hd0,0) and (hd0,2), (hd0,3), (hd0,4) but   WinXP still does not start.

---

### Post by Bucky Ball on 2009-04-15
It is (hd0,0) if it is first partition, first drive. Don't both with the other ones if this is the case. Counting starts from 0, not 1. Therefore (hd0,0) = Disk 1, Partition 1. You will notice your Ubuntu install is on (hd0,2), the third partition?

So that is not the problem. Where did you install grub during the installation?

---

### Post by nguyenthetam on 2009-04-15
> **Bucky Ball said:**
> 

So that is not the problem. Where did you install grub during the installation?

As I remember, the install process did not ask me where to place GRUB (?). Maybe it created GRUB by default (?)

---

### Post by meierfra. on 2009-04-15
The "hal.dll missing" error is usually caused by a wrong entry in boot.ini.

But to get better picture of the situation, I suggest to  boot into  Ubuntu  and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by nguyenthetam on 2009-04-15
Here is Result.txt content:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x23262325

Partition  Boot         Start           End          Size  Id System

/dev/sda1              16,065    41,945,714    41,929,650   f W95 Ext d (LBA)
/dev/sda5    *         16,128    41,945,714    41,929,587   7 HPFS/NTFS
/dev/sda2    *     41,945,715   205,792,649   163,846,935   7 HPFS/NTFS
/dev/sda3         205,792,650   303,451,784    97,659,135  83 Linux
/dev/sda4         303,451,785   312,576,704     9,124,920  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda2: UUID="000CD4720CD46466" LABEL="Data" TYPE="ntfs" 
/dev/sda3: UUID="41d43c1c-e145-439e-a4b2-0dd6f5143d44" TYPE="ext3" 
/dev/sda4: TYPE="swap" UUID="d7c5f554-aba4-41fb-b138-323f456e002b" 
/dev/sda5: UUID="8664A8E064A8D3E9" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/tamnt/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tamnt)


================================ sda5/boot.ini: ================================

[boot loader]
timeout=0
[operating systems]
multi(0)disk(0)rdisk(0)partition(10)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 

================================ sda2/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

C:\="Microsoft Windows" 


=========================== sda3/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=41d43c1c-e145-439e-a4b2-0dd6f5143d44 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=41d43c1c-e145-439e-a4b2-0dd6f5143d44

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root (hd0,2)
uuid		41d43c1c-e145-439e-a4b2-0dd6f5143d44
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=41d43c1c-e145-439e-a4b2-0dd6f5143d44 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		41d43c1c-e145-439e-a4b2-0dd6f5143d44
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=41d43c1c-e145-439e-a4b2-0dd6f5143d44 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		41d43c1c-e145-439e-a4b2-0dd6f5143d44
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Professional - not supported since April 15, 2009
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=41d43c1c-e145-439e-a4b2-0dd6f5143d44 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=d7c5f554-aba4-41fb-b138-323f456e002b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


 142.6GB: boot/grub/menu.lst
 142.5GB: boot/grub/stage2
 142.6GB: boot/initrd.img-2.6.27-7-generic
 142.6GB: boot/vmlinuz-2.6.27-7-generic
 142.6GB: initrd.img
 142.6GB: vmlinuz
```

---

### Post by meierfra. on 2009-04-15
Yes, your "boot.ini" needs to be edited:
Open a terminal in ubuntu and type
```
sudo mount /dev/sda2 /mnt
sudo nano /mnt/boot.ini
```
(don't use "gedit" in place of "nano". gedit does not work well with "dos" files.)

Change  both

partition(2)

to

partition(4)

Follow the instruction at the bottom of the screen to save the file.


Reboot and see whether you can boot into XP.

---

### Post by nguyenthetam on 2009-04-16
meierfra, special thanks !
My XP boots smoothly now and the problem helps me know some interesting things about booting Ubuntu system.:)

---

### Post by meierfra. on 2009-04-16
> My XP boots smoothly now 

Great. Have fun with XP and Ubuntu.

---

