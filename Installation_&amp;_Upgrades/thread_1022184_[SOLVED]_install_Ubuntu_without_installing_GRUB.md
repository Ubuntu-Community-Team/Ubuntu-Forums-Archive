---
title: "[SOLVED] install Ubuntu without installing GRUB"
date: 2008-12-26
forum: Installation &amp; Upgrades
---

### Post by inxygnuu on 2008-12-26
Hello, I am running a dual boot Ubuntu and Vista, and I just got a WD 1TB external drive, and I want to install Ubuntu on it (jaunty), but I don't want it to overwrite the MBR, because I have GRUB configured exactly how In want it. Is there a way to install without installing GRUB?

---

### Post by cariboo on 2008-12-26
Ubuntu always uses the /boot/grub/menu.lst from the last version installed. During the installation stage it will ask you if you want to install grub to the mbr of the first hard disk, just change to install on the disk you are installing ubuntu on, then use something like this in the menu.lst file that you are now using

```
Title		Jaunty Jackalope
UUID 		e4576160-6e8d-4e4d-b5f8-6cf49d655ef9
configfile	/boot/grub/menu.lst
```

To boot from your new installation.

Jim

---

### Post by caljohnsmith on 2008-12-26
Hi inxygnuu, so do you want to avoid overwriting the MBR on the new 1 TB drive, or on another of your drives? You can control where Grub gets installed to by clicking the "advanced" button near the end of the installation process. There you could specify to have Grub installed to the same partition as the partition you are installing Ubuntu (for example), and then the MBR would be untouched. You would do that by choosing "/dev/sdb1" or whichever is the new Ubuntu partition. Let me know how it goes or if you run into problems. :)

---

### Post by inxygnuu on 2008-12-27
> **caljohnsmith said:**
> Hi inxygnuu, so do you want to avoid overwriting the MBR on the new 1 TB drive, or on another of your drives? You can control where Grub gets installed to by clicking the "advanced" button near the end of the installation process. There you could specify to have Grub installed to the same partition as the partition you are installing Ubuntu (for example), and then the MBR would be untouched. You would do that by choosing "/dev/sdb1" or whichever is the new Ubuntu partition. Let me know how it goes or if you run into problems. :)

Oh, wait I have just cleared up some drive space, fixed vista (again), and I am going to install it on /dev/sda, on sdb.  I will lokk into that. thansk for now! (I will tell how it goes soon)

---

### Post by inxygnuu on 2008-12-29
Ok, I just installed Jaunty, and i unchecked "install grub" and I then copied off of ubuntu 8.10 in my menu.lst, but no luck. *bump*

My partition table: (fdisk -l)

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ddd1ddc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3882    31180800    7  HPFS/NTFS
/dev/sda3            3883       24321   164176267+   5  Extended
/dev/sda5   *        4266       13195    71730225    7  HPFS/NTFS
/dev/sda6           19298       24321    40346624    7  HPFS/NTFS
/dev/sda7            3883        4265     3076384+  82  Linux swap / Solaris
/dev/sda8           15210       19297    32836828+  83  Linux
/dev/sda9           13196       15209    16177423+  83  Linux

Partition table entries are not in disk order


menu.lst:

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
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=1869fedd-4125-4bbc-94ff-65c782c2f77c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,7)

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
# defoptions=quiet splash vga=792

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
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1869fedd-4125-4bbc-94ff-65c782c2f77c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1869fedd-4125-4bbc-94ff-65c782c2f77c ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.24-19-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1869fedd-4125-4bbc-94ff-65c782c2f77c ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1869fedd-4125-4bbc-94ff-65c782c2f77c ro  single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,7)
kernel		/boot/memtest86+.bin
quiet

title		Jaunty Jackalope
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.28-3-generic root=UUID=e4576160-6e8d-4e4d-b5f8-6cf49d655ef9 ro quiet splash
initrd		/boot/initrd.img-2.6.28-3-generic
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows
rootnoverify (hd0,0)
chainloader +1

UPDATE: it boots, it just doesn't boot correctly it says some stuff is missing or not found, then drops to an unusual command line shell.

---

### Post by caljohnsmith on 2008-12-29
> **inxygnuu said:**
> 
```
title		Jaunty Jackalope
root		[COLOR="Blue"](hd0,9)[/COLOR]
kernel		/boot/vmlinuz-2.6.28-3-generic root=UUID=e4576160-6e8d-4e4d-b5f8-6cf49d655ef9 [COLOR="Blue"]ro quiet splash[/COLOR] 
initrd		/boot/initrd.img-2.6.28-3-generic
quiet

```

So is Jaunty on sda8 or sda9? sda8 would be (hd0,7) and sda9 would be (hd0,8 ) in Grub's Convoluted World, so (hd0,9) above unfortunately won't work. Also, the "root=UUID=..." line should be on the same line as the "kernel" line, similar to your 8.10 entries (as I've shown above), and don't forget to add the "ro quiet splash" at the end. How about trying that and see if it works, and if not, please run the following bash script:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by cariboo on 2008-12-29
Unless you know what you are doing, Jaunty is really broken right now, none of the restricted drivers work with the latest Xorg servers, so you can only use the open source drivers. I would suggest installing Intrepid, as everything works.

Jim

---

### Post by inxygnuu on 2008-12-29
> **cariboo907 said:**
> Unless you know what you are doing, Jaunty is really broken right now, none of the restricted drivers work with the latest Xorg servers, so you can only use the open source drivers. I would suggest installing Intrepid, as everything works.

Jim

I am using Intrepid to type this. I have it going fine on another computer, I just thought I would try it on a better computer.:)

---

### Post by inxygnuu on 2008-12-29
Okay, I can boot, into it, it just wont work. I think this would be a good time to learn on how to transfer kernel drivers!:o

---

### Post by caljohnsmith on 2008-12-29
Inxygnuu, I think I found your problem; the UUID for your Jaunty partition is wrong in your Grub's menu.lst. How about changing it to:
```
title		Jaunty Jackalope
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.28-3-generic root=UUID=[COLOR="Blue"]b76f39a1-9e0b-4544-9c27-265a5dac603c[/COLOR] ro quiet splash
initrd		/boot/initrd.img-2.6.28-3-generic
quiet
```
Let me know if that works OK.

---

### Post by inxygnuu on 2008-12-29
Thank You! I knew I was missing something, I just didn't know what to put there. :KS:popcorn::D:o:)


[COLOR="Red"]***_[SIZE="7"]THANK YOU!!!![/SIZE]_***[/COLOR]

3v4n

---

### Post by caljohnsmith on 2008-12-30
Glad to hear that worked OK; like Jim basically said though, good luck using Jaunty, it sounds like it could be a challenge to use it at this early point. Cheers and have fun with your OSes. :)

---

### Post by inxygnuu on 2008-12-30
> **caljohnsmith said:**
> Glad to hear that worked OK; like Jim basically said though, good luck using Jaunty, it sounds like it could be a challenge to use it at this early point. Cheers and have fun with your OSes. :)

Actually, Jaunty Alpha 2 is more stable than the Intrepid beta was.:o

Best regards,
3v4n=P~

---

