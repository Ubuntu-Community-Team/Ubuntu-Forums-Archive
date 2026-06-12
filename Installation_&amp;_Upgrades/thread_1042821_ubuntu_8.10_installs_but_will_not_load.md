---
title: "ubuntu 8.10 installs but will not load"
date: 2009-01-17
forum: Installation &amp; Upgrades
---

### Post by pitbull143 on 2009-01-17
Ubuntu installs ok, it just will not completely start. 
I get the following screen it hangs up took a picture of that. I can use the dvd to get it going but the file system is not mounted.I used the dvd mounted the drive found grub and I have also attached that.I added the computer config at the end.
I tried this several times and ended up with 2 primary partions one with root or / on sda and a swap on sdb at the front

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=100233&stc=1&d=1232251774[/IMG] 


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
# kopt=root=UUID=03a628bc-5269-4f56-8a1c-f5f3e2d97f12 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=03a628bc-5269-4f56-8a1c-f5f3e2d97f12

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
uuid		03a628bc-5269-4f56-8a1c-f5f3e2d97f12
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=03a628bc-5269-4f56-8a1c-f5f3e2d97f12 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		03a628bc-5269-4f56-8a1c-f5f3e2d97f12
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=03a628bc-5269-4f56-8a1c-f5f3e2d97f12 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		03a628bc-5269-4f56-8a1c-f5f3e2d97f12
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


drive setup Running bing on all drivesw
(hd0)	/dev/sda ubuntu is here with boot in root
(hd1)	/dev/sdb swap is here at front of drive
(hd2)	/dev/sdc c,d,e,f = raid
(hd3)	/dev/sdd
(hd4)	/dev/sde
(hd5)	/dev/sdf

BOBS TOWER
TYAN THUNDER K7X S2468 UGN / 30 DEVICE DUAL SCSI, DUAL 3COM NIC
(2) 2800 ATHLON MP PROCESSORS
(1) 3 GB RAM
(1) TURTLE BEACH SOUND CARD
(1) RAEDON ATI 8500 DUAL HEAD VID. CARD
(1) 3.5 INCH FLOPPY
(1) PROMISE TX2000 RAID CARD/W
(4) WD IDE 120 GB/W 8 MB BUFFER 7200 RPM = 240GB RAID 0+1
(2) 120 GB IDE 7200 RPM / LINUX on IDE on board	
(2) SAMTRON 19'' MONITORS
(1) 2.1 USB/FIREWIRE A CARD COMBO
(1) DVD-CD R/W 16X ide
(1) DVD-CD R/W 16X ideLIGHTscribe
(1) PANASONIC DVD RAM DISK SCSI
(1) MICROTECH SCANNER SCSI
(1) DUAL SLOT PCI-PCMCIA CARD
(1) HP 7310xi ALL IN ONE USB 2.0
(1) HP 1100 DTN BUS INKJET
(1) 3COM 56K MODEM
(1) MOTOROLA CABLE MODEM
(2) OS's WIN XP PRO/LINUX originally redhat, then mandrake and now ubuntu
    built from sept 1999  to mar 2000

---

### Post by skern03 on 2009-01-17
8.10 is a picky install. I tried four times on this system. Then I got a new case for xmas from my wife (Antec 900, very nice!!!). It was black, and my dvd was cream. Yikes. Bought a new DVD with a black faceplate, and 8.10 installed.

One of the tricks I've used with Ubuntu to get systems to install when they do weird stuff like what you describe is to set the option, noacpi during install.

Here's how:
When you boot from CD, select your language. When you get options to install, run live, etc., Press F6 and type "noacpi" (without the quotes, of course). THEN install Ubuntu. Also, be sure to run checksum - it's possible with the high compression they're using now that the CD is defective.

If that doesn't work, try 8.04. It's a whole lot more forgiving.

Also, I generally choose Manual for partioning, and set it up like so, and in this specific order:
1) mountpoint: root (/) anywhere from 5-20 GB (five is all it really needs), ext3 journaling filesystem. Set it to format the partition.
2) mountpoint: linux swap. No format or filesystem option is available or needed.
3) mountpoint: /home. The rest of the drive, or whatever you want to devote to Linux. Set it to ext3 journaling filesystem, and THE FIRST TIME set it to format. Subsequently, just mount it. That way, you can reinstall without trashing your home directory and settings.

Good luck, and post back if this helps. Or doesn't :)

---

### Post by lavinog on 2009-01-18
it isnt seeing your root partition: UUID=03a628bc-5269-4f56-8a1c-f5f3e2d97f12
it could be a problem with your raid setup.
I am not really familiar with raid installs, but I have had a similar issue with UUIDs in menu.lst being wrong after moving file systems around

---

### Post by Dieseler on 2009-01-18
You could use the Live cd to get in and maybe edit menu.lst to use a symlink to get you into the system.

Heres the how do.
[http://users.bigpond.net.au/hermanzone/p15.htm#3._Symlink](http://users.bigpond.net.au/hermanzone/p15.htm#3._Symlink)

You're system from what I read of you're post looks like this symllink entry below would work.
Cut and paste this in above the other Ubuntu entries and it should be the default or hit escape at the grub and choose it.

> title        Ubuntu 8.10 Symlink Entry so I can get in my box
root         (hd0,0)
kernel       /vmlinuz root=/dev/sda1 ro quiet splash
initrd       /initrd.img
boot

Should work, then you can muck with the rest of it from inside the system itself.
Even if this doesn't work, it can't hurt anything as you can just delete the entry later.

---

### Post by pitbull143 on 2009-01-22
I Looked at the uids and they were the same in grub as the partions. The raid array has a xp partion, a data partion,a xp boot partion and a bing partion. should have no effect on ubuntu, it is located on the first IDE drive on the board and set as 1st device for boot in the bios. Using the live dvd I found that none of partions were mounted and after mounting the advanced properties had no mount points defined.
Thanks

---

### Post by pitbull143 on 2009-01-22
> **Dieseler said:**
> You could use the Live cd to get in and maybe edit menu.lst to use a symlink to get you into the system.

Heres the how do.
[http://users.bigpond.net.au/hermanzone/p15.htm#3._Symlink](http://users.bigpond.net.au/hermanzone/p15.htm#3._Symlink)

You're system from what I read of you're post looks like this symllink entry below would work.
Cut and paste this in above the other Ubuntu entries and it should be the default or hit escape at the grub and choose it.



Should work, then you can muck with the rest of it from inside the system itself.
Even if this doesn't work, it can't hurt anything as you can just delete the entry later.
I used the live dvd and edited grub. Still had the same problem edited grub at boot to change partion. made no difference
Thanks

---

### Post by pitbull143 on 2009-01-22
> **skern03 said:**
> 8.10 is a picky install. I tried four times on this system. Then I got a new case for xmas from my wife (Antec 900, very nice!!!). It was black, and my dvd was cream. Yikes. Bought a new DVD with a black faceplate, and 8.10 installed.

One of the tricks I've used with Ubuntu to get systems to install when they do weird stuff like what you describe is to set the option, noacpi during install.

Here's how:
When you boot from CD, select your language. When you get options to install, run live, etc., Press F6 and type "noacpi" (without the quotes, of course). THEN install Ubuntu. Also, be sure to run checksum - it's possible with the high compression they're using now that the CD is defective.

If that doesn't work, try 8.04. It's a whole lot more forgiving.

Also, I generally choose Manual for partioning, and set it up like so, and in this specific order:
1) mountpoint: root (/) anywhere from 5-20 GB (five is all it really needs), ext3 journaling filesystem. Set it to format the partition.
2) mountpoint: linux swap. No format or filesystem option is available or needed.
3) mountpoint: /home. The rest of the drive, or whatever you want to devote to Linux. Set it to ext3 journaling filesystem, and THE FIRST TIME set it to format. Subsequently, just mount it. That way, you can reinstall without trashing your home directory and settings.

Good luck, and post back if this helps. Or doesn't :)

I tried this at least 4 times (2 120gb drives) started with a swap and root partion ended up with primary swap on second drive and empty unused primary swap on 1st drive (for a third system),logical boot, root, home, user and primary bing partions. I did the "noacpi" option
and it showed up in grub ok but made no difference.

I Looked at the uids and they were the same in grub as the partions. Using the live dvd I found that none of partions were mounted and after mounting the advanced properties had no mount points defined.
I followed your advice, scrubed it and downloaded 8.04 it went ok and is working fine. I also have a HP notebook 8.10  went in there fine and even the wireless works. 
Thanks

---

### Post by skern03 on 2009-01-25
> **pitbull143 said:**
> I tried this at least 4 times (2 120gb drives) started with a swap and root partion ended up with primary swap on second drive and empty unused primary swap on 1st drive (for a third system),logical boot, root, home, user and primary bing partions. I did the "noacpi" option
and it showed up in grub ok but made no difference.

I Looked at the uids and they were the same in grub as the partions. Using the live dvd I found that none of partions were mounted and after mounting the advanced properties had no mount points defined.
I followed your advice, scrubed it and downloaded 8.04 it went ok and is working fine. I also have a HP notebook 8.10  went in there fine and even the wireless works. 
Thanks

Glad 8.04 is working! I had the same thing - 8.10 loaded on an old Dell 8600 with zero hitches, but my desktop was a completely different story.

---

### Post by abn91c on 2009-01-25
```
exit
``` then press enter will get you to the desktop

---

