---
title: "GRUB and XP don't like eachother"
date: 2009-06-04
forum: Installation &amp; Upgrades
---

### Post by Shawn425 on 2009-06-04
Hello, I've recently installed "Windows XP Professional Edition" alongside "Windows XP Home Edition" and "Ubuntu 9.10".
As I expected after installation Windows had replaced GRUB with its own boot-loader.
I followed this guide to re-enable GRUB:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
After following that thread I could boot into Ubuntu and Windows XP Home Edition, but I quickly realized that Windows XP Professional was missing from the list.

After a quick search of Google I discovered that GRUB most likely had no record of this Windows installation, as I had GRUB installed before this Windows installation, I found a guide to fix this here:
[http://www.everyjoe.com/newlinuxuser/adding-other-operating-systems-to-grub/](http://www.everyjoe.com/newlinuxuser/adding-other-operating-systems-to-grub/)
As the guide suggested, I followed it's instructions and added the following to the bottom of menu.lst:
```
title		Windows XP Professional
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1
```
After a quick reboot and a testing of the new menu item I found myself staring at an error message, something along the lines of:
```
NTLDR is missing.
Press CTRL+ALT+DEL to restart.
```
That is when I decided to ask the forums, as I'm inexperienced with this kind of stuff.

Edit:
The Windows XP Professional partition wont give up the "boot" flag.
I booted on to my gParted CD and took away the boot flag and gave it to the Ubuntu partition, but after rebooting into Ubuntu and opening gParted I realized that Professional had the flag again, why would it be doing this?

---

### Post by presence1960 on 2009-06-04
From Ubuntu download the Boot Info Script to your Desktop from : [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Then open a terminal- Applications > Accessories > terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will produce a RESULTS.txt file on your Desktop. Open the file and paste all contents back here. After pasting highlight all text here and click # on the toolbar to place code tags around the text. This will give us a better look at your setup.

---

### Post by zeex on 2009-06-04
> **Shawn425 said:**
> 

After a quick reboot and a testing of the new menu item I found myself staring at an error message, something along the lines of:
```
NTLDR is missing.
Press CTRL+ALT+DEL to restart.
```


Hi, 

You can take a look [here]("http://stringofthoughts.wordpress.com/2009/05/01/ntldr-missing/") for restoring your NTLDR. 

Good luck :)

---

### Post by Shawn425 on 2009-06-04
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu karmic (development 
                       branch)
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   163,959,389   163,959,327   7 HPFS/NTFS
/dev/sda2    *    163,959,390   268,414,019   104,454,630   7 HPFS/NTFS
/dev/sda3         268,414,020   488,279,609   219,865,590  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="3EA8DD9BA8DD51CF" LABEL="XP_HOME" TYPE="ntfs" 
/dev/sda2: UUID="20389ADD389AB0F0" LABEL="XP_PRO" TYPE="ntfs" 
/dev/sda3: LABEL="Ubuntu9.10" UUID="e83f3f4d-c8ee-419c-8922-acdda3989137" TYPE="ext4" 

=============================== "mount" output: ===============================

/dev/sda3 on / type ext4 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/sean/.Private on /home/sean type ecryptfs (ecryptfs_sig=38541c8422b0681d,ecryptfs_fnek_sig=c89181a226445263,ecryptfs_cipher=aes,ecryptfs_key_bytes=16)
gvfs-fuse-daemon on /home/sean/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sean)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=AlwaysOff /fastdetect


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
# kopt=root=UUID=e83f3f4d-c8ee-419c-8922-acdda3989137 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e83f3f4d-c8ee-419c-8922-acdda3989137

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

title		Ubuntu karmic (development branch), kernel 2.6.30-7-generic
uuid		e83f3f4d-c8ee-419c-8922-acdda3989137
kernel		/boot/vmlinuz-2.6.30-7-generic root=UUID=e83f3f4d-c8ee-419c-8922-acdda3989137 ro quiet splash 
initrd		/boot/initrd.img-2.6.30-7-generic
quiet

title		Ubuntu karmic (development branch), kernel 2.6.30-7-generic (recovery mode)
uuid		e83f3f4d-c8ee-419c-8922-acdda3989137
kernel		/boot/vmlinuz-2.6.30-7-generic root=UUID=e83f3f4d-c8ee-419c-8922-acdda3989137 ro  single
initrd		/boot/initrd.img-2.6.30-7-generic

title		Ubuntu karmic (development branch), kernel 2.6.30-6-generic
uuid		e83f3f4d-c8ee-419c-8922-acdda3989137
kernel		/boot/vmlinuz-2.6.30-6-generic root=UUID=e83f3f4d-c8ee-419c-8922-acdda3989137 ro quiet splash 
initrd		/boot/initrd.img-2.6.30-6-generic
quiet

title		Ubuntu karmic (development branch), kernel 2.6.30-6-generic (recovery mode)
uuid		e83f3f4d-c8ee-419c-8922-acdda3989137
kernel		/boot/vmlinuz-2.6.30-6-generic root=UUID=e83f3f4d-c8ee-419c-8922-acdda3989137 ro  single
initrd		/boot/initrd.img-2.6.30-6-generic

title		Ubuntu karmic (development branch), kernel 2.6.30-5-generic
uuid		e83f3f4d-c8ee-419c-8922-acdda3989137
kernel		/boot/vmlinuz-2.6.30-5-generic root=UUID=e83f3f4d-c8ee-419c-8922-acdda3989137 ro quiet splash 
initrd		/boot/initrd.img-2.6.30-5-generic
quiet

title		Ubuntu karmic (development branch), kernel 2.6.30-5-generic (recovery mode)
uuid		e83f3f4d-c8ee-419c-8922-acdda3989137
kernel		/boot/vmlinuz-2.6.30-5-generic root=UUID=e83f3f4d-c8ee-419c-8922-acdda3989137 ro  single
initrd		/boot/initrd.img-2.6.30-5-generic

title		Ubuntu karmic (development branch), memtest86+
uuid		e83f3f4d-c8ee-419c-8922-acdda3989137
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
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

title		Windows XP Pro
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=e83f3f4d-c8ee-419c-8922-acdda3989137 /               ext4    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/mnt/1024Mb.swap  none  swap  sw  0 0

=================== sda3: Location of files loaded by Grub: ===================


 138.7GB: boot/grub/menu.lst
 139.8GB: boot/grub/stage2
 141.1GB: boot/initrd.img-2.6.30-5-generic
 142.8GB: boot/initrd.img-2.6.30-6-generic
 150.0GB: boot/initrd.img-2.6.30-7-generic
 139.8GB: boot/vmlinuz-2.6.30-5-generic
 141.2GB: boot/vmlinuz-2.6.30-6-generic
 149.6GB: boot/vmlinuz-2.6.30-7-generic
 150.0GB: initrd.img
 142.8GB: initrd.img.old
 149.6GB: vmlinuz
 141.2GB: vmlinuz.old

```
The above is the requested RESULTS.txt, I hope it helps.
I will take a look at that link while I await a reply.

Thanks for the fast replies so far!

---

### Post by presence1960 on 2009-06-04
your windows bootloader is definitely not on sda2. you will need to restore it. You can use zeex's link or this one : [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Then you will have to restore GRUB because Windows bootloader will overwrite it. Restore GRUB :

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

Out of curiosity why XP Home & XP Pro? I would think XP Pro would replace XP Home. Just a thought.

---

### Post by Shawn425 on 2009-06-04
Well, I've had no luck with repairing NTLDR from an XP CD.
I tried both my Professional and Home disk, and both times I got the "NTLDR is missing" error instead of either GRUB or NTLDR on the next reboot.
After I booted into my Ubuntu disk and repaired GRUB this went away, but I still can't access my Windows XP Professional OS.

I have no idea what to do now. :(

If you have any bit of information you think would help me, don't hesitate to inform me!

---

### Post by presence1960 on 2009-06-04
> **Shawn425 said:**
> Well, I've had no luck with repairing NTLDR from an XP CD.
I tried both my Professional and Home disk, and both times I got the "NTLDR is missing" error instead of either GRUB or NTLDR on the next reboot.
After I booted into my Ubuntu disk and repaired GRUB this went away, but I still can't access my Windows XP Professional OS.

I have no idea what to do now. :(

If you have any bit of information you think would help me, don't hesitate to inform me!

Well you can always reinstall XP PRO. I know that is a pain. Or just use XP Home. Or get rid of XP Home and reinstall XP Pro on sda1

---

### Post by raymondh on 2009-06-04
> **Shawn425 said:**
> Well, I've had no luck with repairing NTLDR from an XP CD.
I tried both my Professional and Home disk, and both times I got the "NTLDR is missing" error instead of either GRUB or NTLDR on the next reboot.
After I booted into my Ubuntu disk and repaired GRUB this went away, but I still can't access my Windows XP Professional OS.

I have no idea what to do now. :(

If you have any bit of information you think would help me, don't hesitate to inform me!

From what I've been reading ... a missing NTLDR error could *also* stem from a corrupted boot.ini file.  See if this link may help.

[http://pcsupport.about.com/od/findbyerrormessage/a/ntldrmissingxp.htm](http://pcsupport.about.com/od/findbyerrormessage/a/ntldrmissingxp.htm)
[http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm)

As for booting, it may be because of a missing hal.dll in the boot.ini.  See this link as well.

[http://srivigneshwar.com/blog/2008/12/15/missing-haldll-after-ubuntu-installationcannot-boot-xp/](http://srivigneshwar.com/blog/2008/12/15/missing-haldll-after-ubuntu-installationcannot-boot-xp/)

I have never done this.  They may be options for you to ponder on or try.

Good luck.

---

### Post by Shawn425 on 2009-06-04
Here is what happened:
At the GRUB bootloader I selected Windows XP Home Edition.
The NTLDR appeared, allowing me to choose between Windows XP Home Edition and Windows XP Professional Edition
I booted into Professional, and I'm posting from it right now.
The Windows XP Professional Edition option at the GRUB still doesn't work.

This is all very confusing to me, given this new information do you have any new ideas?

---

### Post by presence1960 on 2009-06-05
I have never used 2 or more versions of Windows at once. Maybe that is the way it is supposed to be: boot into XP Home and have the option to choose Home or Pro. Maybe someone here who has dual or triple booted Windows can help you out further here. At least you can get Home & PRO to boot.

P.S. I can't imagine 2 windows installs on my machine, one is too many!!

---

