---
title: "Vista &amp; Ubuntu Duel Boot - External USB Hardrive (2 partitions)"
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by GodsDead on 2008-12-16
Hey all i have been using ubuntu server for a while, so im comftable with hackign and coding. thigns is im scared to try this as i cant lose anyhtign on my windows vista instillation.
So boom! i bought a 500gb External HDD, which i would like to install ubuntu desktop on.

Iv done a bit of research but only confized myself, i hear that after installing Ubuntu onto the external HDD, nothing boots if the external HDD is not connected?
I hear a faint answer of A mod for grub on the internal? or a super grub on the external?
That would be great to clearup! espicially with a tutorial! =p

Also, i would like to partition my external HDD, say give 50gb to ubuntu to play with, and the rest im gonna use as backup (NTFS) for winhoes =p

Would i use the Vista partition editor or the one in ubuntu?

CHEERS!!


Oh, and im probily going to do a witeup in my blog, so any help will be documented, so include your website if you want props XD =p

---

### Post by logos34 on 2008-12-16
here you go:

[http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/](http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/)

(works for flash drives and external usb hard drives)

At the partitioning stage you can choose 'Guided install -- use entire disk' and then use Gparted later to shrink it down to make room for ntfs partition, or select 'manual' and create / and /swap the desired size. 

Actually, it might be best to partition it with gparted on the live cd desktop before you click the install icon.  >system>admin>partition editor.

create an ext3 / and /swap (linux-swap).  then make ntfs on rest.   now do the install

---

### Post by GodsDead on 2008-12-16
Ah great, thanks, ill do this tomorrow when im not so tired, i mean this is a bit extreme:
> 
Important: Physically disconnect ALL internal hard drives before booting from the CD and performing the install. this will eliminate the possibility of installing to the wrong device and overwriting your MBR. Reattach the drives after completing this tutorial.

But funny enough i bought a internal card reader today that i need to install! ha

Also wouldnt this just boot whatever device is set to top prioraty from my BIOS?
Or would i have to set this external drive in BIOS as the Top drive?

If so, then do i have to edit something for it to pick up vista from my other HDD?

And would thi scause any problems when booting without the USB HDD plugged in?

---

### Post by albinootje on 2008-12-16
> **GodsDead said:**
> 
Also wouldnt this just boot whatever device is set to top prioraty from my BIOS?
Or would i have to set this external drive in BIOS as the Top drive?


You are advised to put the external usb drive as first.
But some computers have a boot-menu option, like F12, which you can use to make your choice about which device should boot.

---

### Post by GodsDead on 2008-12-17
OK, i unplugged my main HDD, and installed Ubuntu to my external HDD on its own 30gb partition, and booting up grub errors this:
```

Grub loading stage 1.5.

Grub loading, please wait...
Error 18

```

---

### Post by albinootje on 2008-12-17
See here for more details about Grub error 18 : [http://wiki.linuxquestions.org/wiki/GRUB#Error_18](http://wiki.linuxquestions.org/wiki/GRUB#Error_18)

It could be an idea to reinstall it and define a separate /boot directory to encounter this problem. 
(Make sure you don't attach your real hard disk during the installation on the usb disk).

---

### Post by GodsDead on 2008-12-18
Yea i was thinking about a re-install, You can select in (advanced) where you want the boot to load.. but it had many options like / /root and tonnes more i cant remember, and then also where to install to like hda1 and stuff there was about 2/3 even though i only had on USB external HDD plugged in, so i just left this all as default something lie hda0 ?

---

### Post by logos34 on 2008-12-18
> **GodsDead said:**
> Yea i was thinking about a re-install, You can select in (advanced) where you want the boot to load.. but it had many options like / /root and tonnes more i cant remember, and then also where to install to like hda1 and stuff there was about 2/3 even though i only had on USB external HDD plugged in, so i just left this all as default something lie hda0 ?

If you have only one hdd plugged in during installation, there is only one place the Grub bootloader can go by default, and that's (hd0), i.e the MBR of the USB drive.  Grub appears at boot (stage1), but for some reason it's having trouble finding the / partition (specifically /boot/grub/menu.lst).

---

### Post by Mark Phelps on 2008-12-18
Would suggest the following ...

Plugin the USB drive with Ubuntu on it.

Boot from a LiveCD (with both hard drives connected and running).

Do an "fdisk -lu" (that's a lower-case ell, not a one).

Don't be surprised if Linux shows both an "hd" and "sd" drives.

My guess is that when you installed Ubuntu, GRUB installed to "hd0" but when the USB drive and the internal driver are both connected, it sees the USB drive as "sd0".  If that's the case, modify the /boot/grub/menu.lst file to boot Linux from "sd0" instead of "hd0".

---

### Post by logos34 on 2008-12-18
> **Mark Phelps said:**
> 
My guess is that when you installed Ubuntu, GRUB installed to "hd0" but when the USB drive and the internal driver are both connected, it sees the USB drive as "sd0".  If that's the case, modify the /boot/grub/menu.lst file to boot Linux from "sd0" instead of "hd0".

you've got the grub terminology wrong--see Grub Page link in my signature.

---

### Post by GodsDead on 2008-12-19
Ah great, im starting to understand a little better now..
But still stuck on what i have to do to fix this in the /boot/grub/menu.lst

I have never worked with this before!
Most things are hashed out, so i take it there not in operation..

This is my menu.lst
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
# kopt=root=UUID=0aadba4f-a5f9-4d53-887a-d23db482aa7d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0aadba4f-a5f9-4d53-887a-d23db482aa7d

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
uuid		0aadba4f-a5f9-4d53-887a-d23db482aa7d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0aadba4f-a5f9-4d53-887a-d23db482aa7d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		0aadba4f-a5f9-4d53-887a-d23db482aa7d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0aadba4f-a5f9-4d53-887a-d23db482aa7d ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		0aadba4f-a5f9-4d53-887a-d23db482aa7d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

And with both HDD's connected and running this VIA the live CD
Inputting sudo fdisk -fu outputs these; (bearing in mind i also have a internal card reader if that helps?)
```

sudo fdisk -lu

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf4eff4ef

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   490231807   245114880    7  HPFS/NTFS

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009d9ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *          63   912443804   456221871    7  HPFS/NTFS
/dev/sdf2       912443805   976768064    32162130    5  Extended
/dev/sdf5       912443868   974020949    30788541   83  Linux
/dev/sdf6       974021013   976768064     1373526   82  Linux swap / Solaris


```

---

### Post by logos34 on 2008-12-19
Well, you're even using the new 8.10 menu.lst, which uses UUIDs exclusively, so it can't be an error on the 'root' line, as is sometimes the case...And unless you have a very old Bios it can't be a cylinder limit issue, so I doubt making a separate /boot toward the front of the disk will help, although it's always[ a possibility]("http://users.bigpond.net.au/hermanzone/p15.htm#18"). You might try different hdd detect settings in the Bios.

If that doesn't work, you could try [booting the kernels from the internal hdd]("https://help.ubuntu.com/community/BootFromUSB")...you won't have to worry about it not starting when the external usb is disconnected either

---

### Post by GodsDead on 2008-12-22
I dont get it :S
my computers fairly recent and its got the latest bios updates (and yea vista didnt like that!)
But i mean, if its just my External HDD and the main isnt plugged in, the errors there.
Im gonna try a re-install, but this time with my Main HDD plugged in..
Seems a little stupid, since it probily installed fine, its just getting it to boot :/

can i ask, does the uuid in grub/root store which HDD it boots from?

Although, without the main HDD theres only one place grub can go.. and thats the external, and grub loads Argh :/

---

### Post by GodsDead on 2008-12-22
Well i completed a re-install.. and yea same error, this time i did it with both HDD's connected, and in teh advanced tab chose the partition to where the instillation was going to happen (sdb5).
And booted that drive up and nah, it dousnt like it lol

---

### Post by logos34 on 2008-12-22
> **GodsDead said:**
> Well i completed a re-install.. and yea same error, this time i did it with both HDD's connected, **and in teh advanced tab chose the partition to where the instillation was going to happen (sdb5)**.
And booted that drive up and nah, it dousnt like it lol

that won;t work because you need grub on the MBR, which is what the Bios looks for at bootup (i.e. the IPL in the first sector of the hard disk), which in turn looks for the root partition containing menu.lst.  

> Although, without the main HDD theres only one place grub can go.. and thats the external, and grub loads Argh :/
yep, that's the theory at least!

---

### Post by GodsDead on 2008-12-22
So, do you think manually editing the grub files would get me somewhere?
I dont know what to do, unless i play with the vista boot menu? 
I think it has one..?

---

### Post by logos34 on 2008-12-22
> **GodsDead said:**
> So, do you think manually editing the grub files would get me somewhere?
I dont know what to do, unless i play with the vista boot menu? 
I think it has one..?

what i'd try next is the method in the link i gave in post #12 above or maybe use EasyBCD and add a [linux entry with NeoGrub]("http://neosmart.net/wiki/display/EBCD/Linux").

good luck

---

