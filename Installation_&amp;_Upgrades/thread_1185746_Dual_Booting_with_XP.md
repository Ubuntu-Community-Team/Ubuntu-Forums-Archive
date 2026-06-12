---
title: "Dual Booting with XP"
date: 2009-06-12
forum: Installation &amp; Upgrades
---

### Post by carterw65 on 2009-06-12
Hello Everyone!

I have installed Ubuntu 9.04 on my WinXP drive. I formatted the drive with the following partitions:

WinXp
Ubuntu
Swap
Fat32

I tried to install it without the Grub and no luck. Tried it with the Grub and no luck (current install). I have got to the point where upon boot I can select either XP or Ubuntu. When I select Ubuntu it just sits there and does nothing. Here is my boot record in XP:

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn
c:\ubuntu.bin="Ubuntu Linux"

Any ideas???

Thanks!   :confused:

---

### Post by martiendejong on 2009-06-12
What I did was install XP first, then Ubuntu.
Then I created a multiboot using Grub.
I used this tutorial more or less: 
[http://tldp.org/HOWTO/Multiboot-with-GRUB.html]("http://tldp.org/HOWTO/Multiboot-with-GRUB.html")

In your ubuntu partition there should be a file /boot/grub/menu.lst
If you change that file according to the tutorial it should all work.

Success,
Martien

---

### Post by carterw65 on 2009-06-12
The howto refers to Win98. I don't own a floppy drive and frankly I am a dummy when it comes to linux. Can you be more specific on what you think is going on. 

I used this [http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/) to configure my system and it didn't work.

Thanks

---

### Post by merlinus on 2009-06-12
You would probably be far better off using grub to boot both ubuntu and xp.

Follow these instructions for installing grub using the live ubuntu cd:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by carterw65 on 2009-06-17
This worked awesome with grub and a fresh 9.04 install. I couldn't get it to work with a back up image though. I took an image of my Ubuntu drive and installed it on the ext3 partition of my dual boot drive and couldn't get it to work at all.

---

### Post by carterw65 on 2009-07-13
I finally got Ubuntu to boot with the Super Grub cd. But I can't get it to dual boot properly. When I try to use the Super Grub cd to fix the boot it says it can't mount and gives an error of 17. 

So at this point I have to use Super Grub cd to boot. Here is my menu.lst output:

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
# root		(hd0,0)
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
# kopt=root=UUID=e5c74164-a84a-4f74-a6db-6e42c67f8bbc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=e5c74164-a84a-4f74-a6db-6e42c67f8bbc ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=e5c74164-a84a-4f74-a6db-6e42c67f8bbc ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=e5c74164-a84a-4f74-a6db-6e42c67f8bbc ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=e5c74164-a84a-4f74-a6db-6e42c67f8bbc ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 9.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


Any ideas?  Thanks!

Bill:confused:

---

### Post by merlinus on 2009-07-13
Post results of

```
sudo fdisk -l
```

---

### Post by carterw65 on 2009-07-14
> **merlinus said:**
> Post results of

```
sudo fdisk -l
```


Here are the results:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaafb0b21

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8950    71890843+   7  HPFS/NTFS
/dev/sda2           15330       15592     2112547+   5  Extended
/dev/sda3            8951       15329    51239317+  83  Linux
/dev/sda4           15593       19457    31045612+   b  W95 FAT32
/dev/sda5           15330       15592     2112516   82  Linux swap / Solaris

Partition table entries are not in disk order


sda1 is my winXP partition (which grub doesn't currently see), Not sure what sda2 is, sda3 is Ubuntu, sda4 is a Fat32 partition that I created so both Ubuntu and XP can access it, sda5 is the swap file.

Thanks!

---

### Post by merlinus on 2009-07-14
Add this to the very end of menu.lst:

title Windows
rootnoverify (hd0,0)
makeactive
chainloader +1

and restart.

Also post tesults of

```
sudo blkid
```

---

### Post by carterw65 on 2009-07-14
merlin,

I really appreciate your help with this. I pasted the entry into menu.lst and rebooted. One problem with it was that grub tried to boot directly to Ubuntu first, when it failed it gave me a menu to select Windows which now does show up as an option and indeed does work. How do I change the grub to offer the menu first without trying to boot first?

Here is the failure output:

Booting 'Ubuntu 9.04, kernel 2.6.28-13-generic
root (hd0,0)
Filesystem type unknown, partition type 0x7
kernel /boot/umlinuz-2.6.28-13-generic root =UUID=e5c74164-a84a-4f74-a6db-6e42c
67f8bbc ro quiet splash
Error 17: cannot mount selected partition

press any key to continue.....


Then it will give me a boot menu. But still will not let me boot to Ubuntu because of the above failure.

Here is the output from sudo blkid:

/dev/sda1: UUID="4C18D5EE18D5D754" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="20f5e5fb-ca7d-4928-a5b3-39f1f249626e" 
/dev/sda3: UUID="e5c74164-a84a-4f74-a6db-6e42c67f8bbc" TYPE="ext3" 
/dev/sda4: UUID="9692-AA78" TYPE="vfat" 


Thanks a million!

---

### Post by merlinus on 2009-07-14
For starters, change all instances in these stanzas from root (hd0,0) to

root (hd0,2)

title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=e5c74164-a84a-4f74-a6db-6e42c67f8bbc ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=e5c74164-a84a-4f74-a6db-6e42c67f8bbc ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=e5c74164-a84a-4f74-a6db-6e42c67f8bbc ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=e5c74164-a84a-4f74-a6db-6e42c67f8bbc ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 9.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

---

### Post by carterw65 on 2009-07-14
merlin,

You are an Ubuntu Wizard in my book. Changing from (hd0,0) to (hd0,2) worked perfectly. I upgraded to 2.6.28-13-generic since the postings so I changed those entries as well.

I am completely lost as to how you knew to do that though. I understand the partitions and the hd, sda, sdb etc... Can you give me some explanation, I would appreciate it.

If I hit esc quick enough I can get it to the grub menu before it boots. I didn't have to do that before, it always went straight to grub. Is there a setting I can change somewhere.

Thanks again,

Bill

---

### Post by merlinus on 2009-07-14
Glad things are working.  Ubuntu is on sda3, which translates to (hd0,2).  Numbering for these kinds of things begins at 0 (zero).

You can increase the timeout to 10 in menu.lst -- it is now 3:

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

If you set it to 0 the only way the grub menu will appear is if you press Esc fast enough!

Also this setting:

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

hides grub completely.  If you want to see the menu on bootup, place a hashmark (#) in front of hiddenmenu on the third line.

---

### Post by presence1960 on 2009-07-14
> **carterw65 said:**
> merlin,

You are an Ubuntu Wizard in my book. Changing from (hd0,0) to (hd0,2) worked perfectly. I upgraded to 2.6.28-13-generic since the postings so I changed those entries as well.

I am completely lost as to how you knew to do that though. I understand the partitions and the hd, sda, sdb etc... Can you give me some explanation, I would appreciate it.

If I hit esc quick enough I can get it to the grub menu before it boots. I didn't have to do that before, it always went straight to grub. Is there a setting I can change somewhere.

Thanks again,

Bill
here is your sudo fdisk -l output:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaafb0b21

Device Boot Start End Blocks Id System
/dev/sda1 * 1 8950 71890843+ 7 HPFS/NTFS
/dev/sda2 15330 15592 2112547+ 5 Extended
/dev/sda3 8951 15329 51239317+ 83 Linux
/dev/sda4 15593 19457 31045612+ b W95 FAT32
/dev/sda5 15330 15592 2112516 82 Linux swap / Solaris

Partition table entries are not in disk order




```

Hard disks are labeled like this: first disk = sda, second disk = sdb, etc
partitions are labeled like this: first disk/first partition sda1, first disk/second partition sda2, etc

windows is on sda1, Ubuntu is on sda3.

When you use GRUB the numbering goes like this: it starts at 0 for both hard disks & partitions. So your windows is on sda1, that translates to (hd0,0) where (hdx,y). x = disk, y = partition. first disk is 0, first partition is 0- hence (hd0,0) for windows.

Now for Ubuntu. It is on sda3. So we have (hd0,2) where 0 = first disk and 2 = third partition.

In GRUB numbering always starts at 0.
Welcome to Ubuntu and enjoy. Merlin is knowledgable BTW  :popcorn:

---

### Post by carterw65 on 2009-07-14
That all makes total sense to me. I am a network tech by trade, but I am a WAN guy, so I don't get to play with the computers too much and we use, sigh....windows. 

Anyway, everything is working just fine now. BTW, if anyone cares, I used "Clonezilla" to copy Ubuntu from it's old drive onto the new partition of my new drive. There are a few, very few, things I still use Windows for so I wanted it to dual boot rather than swapping hard drives in and out of my system.

Thanks a ton, I am well pleased!

---

