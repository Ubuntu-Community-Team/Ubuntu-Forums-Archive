---
title: "[SOLVED] Can't boot both Ubuntu and XP from grub"
date: 2008-11-02
forum: General Help
---

### Post by edwinlin88 on 2008-11-02
Hi guys,
I have 3 hard drives. One with XP installed,one with Ubuntu installed and one just to hold files.
My problem is when I set my BIOS to detect the hard drive with XP on it first,grub doesnt load therefore I don't get the option of bootings ubuntu.
When I set BIOS to detect the hard drive with Ubuntu first, grub loads and I get the options for both OS but when i choose XP, I get the error NTLDR missing, alt+ctrl+del to restart.
From reading other forum posts I'm pretty sure I have to do something with the grub settings but I am new (first day using) to linux/ubuntu.
Could some1 please help me out?

Thanks

---

### Post by overdrank on 2008-11-02
> **edwinlin88 said:**
> Hi guys,
I have 3 hard drives. One with XP installed,one with Ubuntu installed and one just to hold files.
My problem is when I set my BIOS to detect the hard drive with XP on it first,grub doesnt load therefore I don't get the option of bootings ubuntu.
When I set BIOS to detect the hard drive with Ubuntu first, grub loads and I get the options for both OS but when i choose XP, I get the error NTLDR missing, alt+ctrl+del to restart.
From reading other forum posts I'm pretty sure I have to do something with the grub settings but I am new (first day using) to linux/ubuntu.
Could some1 please help me out?

Thanks

Hi and welcome, I am no grub expert but it appears the grub is installed on the driver with ubuntu. This is for the issue of selecting windows from the grub and not being able to boot as it should have been install on the MBR with the windows partition. This link may help
[http://ubuntuforums.org/showthread.php?t=542683](http://ubuntuforums.org/showthread.php?t=542683)
And this link may help with the grub also
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by caljohnsmith on 2008-11-02
With all due respect to Overdrank :), I personally would not recommend installing Grub to the MBR of your Windows drive since you can all ready successfully boot your Ubuntu drive on start up; all you should need to do is modify your Grub's menu.lst so you can correctly boot Windows. Can you boot into Ubuntu OK from the Grub menu?

How about opening a terminal (applications > accessories > terminal) either from your Live CD or your Ubuntu install if you can boot into it, and first posting:
```
sudo fdisk -lu
```
And if you can boot into your new Ubuntu install, also please post:
```
cat /boot/grub/menu.lst
```
And we can work from there.

---

### Post by edwinlin88 on 2008-11-02
hi thanks for the reply caljohnsmith and overdrank,

my code for sudo fdisk -lu is:
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8b798b79

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   224829674   112414806   83  Linux
/dev/sda2       224829675   234436544     4803435    5  Extended
/dev/sda5       224829738   234436544     4803403+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8c1d536e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   488392064   244196001    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x20001fff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   976751999   488375968+   7  HPFS/NTFS
```


my code for cat /boot/grub/menu.lst is :

```
Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x20001fff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   976751999   488375968+   7  HPFS/NTFS
edwin@edwin-new:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=4a3224d9-1b76-4961-aee3-44501ad326c2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4a3224d9-1b76-4961-aee3-44501ad326c2

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
uuid		4a3224d9-1b76-4961-aee3-44501ad326c2
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4a3224d9-1b76-4961-aee3-44501ad326c2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		4a3224d9-1b76-4961-aee3-44501ad326c2
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4a3224d9-1b76-4961-aee3-44501ad326c2 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		4a3224d9-1b76-4961-aee3-44501ad326c2
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

```

---

### Post by caljohnsmith on 2008-11-02
Looks like your problem might be easy to solve; first pull up your menu.lst with:
```
gksudo gedit /boot/grub/menu.lst
```
And at the bottom add the following:
```
title		Microsoft Windows XP Professional
root		(hd1,0)
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```
Give that a shot, and if it doesn't work, let me know exactly what happens when you try it from the Grub menu. Otherwise let me know how it goes. :)

---

### Post by edwinlin88 on 2008-11-02
at the bottom of my menu.lst I had this already:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1
```

and then I added the code you suggested under this, caljohnsmith. I'll give it a reboot.

---

### Post by edwinlin88 on 2008-11-02
Thanks it worked! but now I have two WinXP options in grub boot menu. I guess I just need to delete the old WinXP boot instructions and replace with the new code I just added?

---

### Post by caljohnsmith on 2008-11-02
> **edwinlin88 said:**
> Thanks it worked! but now I have two WinXP options in grub boot menu. I guess I just need to delete the old WinXP boot instructions and replace with the new code I just added?
Yes, I should have said "replace" instead of "add" in my previous post. Glad it works; cheers and have fun. :)

---

