---
title: "XP Does not show up in Grub Menu!"
date: 2009-08-28
forum: Installation &amp; Upgrades
---

### Post by Teclas5 on 2009-08-28
Hi all. I installed xp and after rebooting, grub does not list it as a choice. I really dont know what to do. :confused: Does anybody have an idea i can try to get it listed again? Any help would be appreciated.

---

### Post by denver on 2009-08-28
Try this:

[http://ubuntuforums.org/showthread.php?t=1252251](http://ubuntuforums.org/showthread.php?t=1252251)

---

### Post by Teclas5 on 2009-08-28
Thanks for the advice denver! I did read that post and tried out your idea, and still it does not show up. :( Any other ideas you might have?

---

### Post by denver on 2009-08-28
Providing that you did not format your Ubuntu install and/or your /bot partition, and you replaced (hd0,5) with your result, it should have worked.

Would give me a better ideea of what went wrong if you could get back with the output of those commands, as well as your disk/partition layout.

---

### Post by denver on 2009-08-28
I have attached a small script that should install grub on all relevant disks for you.

Download it and in a terminal (using a live CD) run it:

```
sudo chmod 755 && sudo ./grub.sh
```

See if that helps.

---

### Post by Teclas5 on 2009-08-28
Thanks for your help with a still learning novice! I tried your script and i got this:

ubuntu@ubuntu:~$ sudo chmod 755 && sudo ./grub.sh
chmod: missing operand after `755'
Try `chmod --help' for more information.
ubuntu@ubuntu:~$ 

I downloaded it while on the live disk to the desktop. Should i have saved it before using the live disk?

---

### Post by denver on 2009-08-28
sorry about that.My bad...i forgot to specify the filename after the chmod command.

It should have been:

chmod 755 grub.sh && sudo ./grub.sh

Asuming that the script is in your current working directory. The script should work if you made a separate /boot partition.

If not you may need to edit it and change:

```
BIOS_DEVICES=`echo 'find /grub/stage1' | grub --read-only --no-curses 2>/dev/null | sed '/(hd/!d;s/(hd//;s/)//;s/^ //'`
```

into

```
BIOS_DEVICES=`echo 'find /boot/grub/stage1' | grub --read-only --no-curses 2>/dev/null | sed '/(hd/!d;s/(hd//;s/)//;s/^ //'`
```

good luck!

---

### Post by presence1960 on 2009-08-28
> **Teclas5 said:**
> Hi all. I installed xp and after rebooting, grub does not list it as a choice. I really dont know what to do. :confused: Does anybody have an idea i can try to get it listed again? Any help would be appreciated.

Let's get a better look at your setup. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Teclas5 on 2009-08-29
Apologies for taking so long, kids are quite a handful. Still no luck with the corrected script you asked me try denver, but i cant rule out novice ignorance on my part. I tried your suggestion presence1960, and the output was:
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

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

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x83748374

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   400,387,994   400,387,932  83 Linux
/dev/sda2         400,387,995   482,399,819    82,011,825   7 HPFS/NTFS
/dev/sda3         482,399,820   488,392,064     5,992,245   5 Extended
/dev/sda5         482,399,883   488,392,064     5,992,182  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8f9c798a

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   312,577,229   312,577,167   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="0112b47f-0021-4901-989f-607272e2a16f" TYPE="ext3" 
/dev/sda2: UUID="C68A09FC8A09E9AF" TYPE="ntfs" 
/dev/sda5: UUID="104b3b04-fcf9-44e2-9197-8551c7a6eddf" TYPE="swap" 
/dev/sdb1: UUID="0E80AA7626166A12" TYPE="ntfs" 

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
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ernesto/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ernesto)
/dev/sdb1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


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
# kopt=root=UUID=0112b47f-0021-4901-989f-607272e2a16f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0112b47f-0021-4901-989f-607272e2a16f

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

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		0112b47f-0021-4901-989f-607272e2a16f
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=0112b47f-0021-4901-989f-607272e2a16f ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		0112b47f-0021-4901-989f-607272e2a16f
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=0112b47f-0021-4901-989f-607272e2a16f ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		0112b47f-0021-4901-989f-607272e2a16f
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=0112b47f-0021-4901-989f-607272e2a16f ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		0112b47f-0021-4901-989f-607272e2a16f
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=0112b47f-0021-4901-989f-607272e2a16f ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.27-14-generic
uuid		0112b47f-0021-4901-989f-607272e2a16f
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=0112b47f-0021-4901-989f-607272e2a16f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode)
uuid		0112b47f-0021-4901-989f-607272e2a16f
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=0112b47f-0021-4901-989f-607272e2a16f ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 9.04, memtest86+
uuid		0112b47f-0021-4901-989f-607272e2a16f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0112b47f-0021-4901-989f-607272e2a16f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=104b3b04-fcf9-44e2-9197-8551c7a6eddf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 165.2GB: boot/grub/menu.lst
 165.3GB: boot/grub/stage2
 165.3GB: boot/initrd.img-2.6.27-14-generic
 165.2GB: boot/initrd.img-2.6.28-14-generic
 165.3GB: boot/initrd.img-2.6.28-15-generic
 165.3GB: boot/vmlinuz-2.6.27-14-generic
 165.2GB: boot/vmlinuz-2.6.28-14-generic
 165.3GB: boot/vmlinuz-2.6.28-15-generic
 165.3GB: initrd.img
 165.2GB: initrd.img.old
 165.3GB: vmlinuz
 165.2GB: vmlinuz.old

================================ sda2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```


Also, thanks for showing me how to put that up properly!

---

### Post by presence1960 on 2009-08-29
Boot into Ubuntu and open a terminal. run this command ```
gksu gedit /boot/grub/menu.lst
``` that is a lowercase L in .lst

Scroll down to this line: ### END DEBIAN AUTOMAGIC KERNELS LIST


add this after the above line

```
title          Windows XP
rootnoverify   (hd0,1)
chainloader    +1
```

also if you want the GRUB menu to appear at boot without hitting Esc change the line in red 

=========================== sda1/boot/grub/menu.lst: ===========================
```

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
[COLOR="Blue"]timeout		3[/COLOR]

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR="Red"]hiddenmenu[/COLOR]
```

to #hiddenmenu

If you don't want GRUB to appear you have 3 seconds to hit ESC once GRUB loading message appears at boot. You can change that by editing the line in blue by changing the numeric value which represents seconds.

click save at the top toolbar and close the file.

Reboot & select windows XP when GRUB menu appears

---

### Post by Teclas5 on 2009-08-29
Thanks a bunch presence1960! That solved my problem :P. I am making an effort to learn, but thankfully, i have had so few problems since switching over to Ubuntu that it leaves little for me to learn from mistakes. Either way, thank you and karma for you and denver for helping me out!  :guitar:

---

### Post by presence1960 on 2009-08-29
> **Teclas5 said:**
> Thanks a bunch presence1960! That solved my problem :P. I am making an effort to learn, but thankfully, i have had so few problems since switching over to Ubuntu that it leaves little for me to learn from mistakes. Either way, thank you and karma for you and denver for helping me out!  :guitar:

No problem, glad you got it working. Enjoy ubuntu!

---

