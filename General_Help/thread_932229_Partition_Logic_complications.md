---
title: "Partition Logic complications"
date: 2008-09-28
forum: General Help
---

### Post by laurenipsum on 2008-09-28
Used to be on dual-boot, until I did something stupid.

I wanted to shrink my Windows partition from about 50 gig to 40 gig using Partition Logic. When I started it up, it told me about errors in XXXXXXXX, proceed with caution, etc. I've been getting disk error messages for the past few days so this wasn't new. I went ahead anyway. 

I had the following partitions:
A. Windows file system - 50 gigs
B. Ubuntu Linux (Hardy) file system - about 10 gigs
C. Swap partition - 1 gig
D. NTFS partition 1
E. NTFS partition 2
F. FAT32 partition - about 10 gigs
G. Plus: This mysterious unused 10 gig chunk that I never got to format for some reason, even when I used Hardy's partitioning during its installation a while back.

Partition Logic detected only the following partitions:
A. Windows (primary)
B. Linux (primary)
D. NTFS Partition 1 (logical)
E. NTFS Partition 2 (logical)
G. Mystery partition (?) 

I didn't find it weird that Partition Logic didn't detect my swap disk and F. Anyway I *still *went ahead and did the ff:
A. Windows - Resized both partition and filesystem 
B. Linux - Left alone
D. NTFS Partition 1  - Left alone
E. NTFS Partition 2 - Left alone
G. Mystery partition - Tried to create a partition but failed because of errors 

Since I now had 10 gigs free, I created a new partition. So here's my list of partitions so far, according to the program:
A. Windows (primary)40 gig
<< H. NEW PARTITION (primary) 10 gig >>
*Note: I've no idea why it was designated as "primary." The option to choose between primary/logical was disabled when I was formatting it.
B. Linux (primary)
D. NTFS Partition 1 (logical)
E. NTFS Partition 2 (logical)
G. Mystery partition (?)

I rebooted, then it all went bonkers. 
- GRUB wouldn't start, stating error xx. 
- So I booted from a Hardy Live CD and reinstalled GRUB. It loaded fine at startup, but whatever OS I chose it wouldn't load correctly.
- I tried the Hardy Live CD again. It was able to detect an unnamed 10 gig drive and browsing the files I found it to be my Linux filesystem. My Home files were still there, thank God. Live Hardy detected the other drives but couldn't mount them except for the NTFS partitions.
- I reinstalled Win XP on the 40 gig partition. It works, but now I don't know how to get to my Ubuntu files. I don't want to reinstall yet because I still have some very important files in my Home folder.

The week's just started and I've already wreaked havoc on my computer. Help?

---

### Post by TeXtonyx on 2008-09-28
Well there is LinuxReader which displays Linux partitions *from* XP, and then lets you
save files from the Linux Partition back to XP, but that would be a bit laborious. Then
there is Super Grug disk, floppy or cd, which boots up and lets you choose a partition 
to boot and it will as long as it is still bootable. Then there is the live cd where you can 
open a terminal and type,  sudo fdisk -l which will show all your partitions. Often one can
tell by the size (10gig) which one you want. Then one can mount that partition with
sudo mount /dev/sda? /mnt then cd /mnt then ls to see if it is your files right location
 (the ? means use a choice from the fdisk report for example sda7).
The way I'd tackle this is code: sudo apt-get ntfs-config install , then sudo ntfs-config
This makes a mount point under /media/???? call it WindowsXP and puts it on your
desktop. double-click and make an XP folder, UbuntuRescue. Now open another 
file browser window and navigate to where you have important files. Keep both open
and you can drag and drop from the Ubuntu locations to the XP rescue folder. Then 
again I think you can burn cds from the live install, once you know where files are and
mount them. Do not despair, all is not lost, look for the solution arriving at the third
day at dawn since it is always darkest before the dawn when eyes are at their most blurry :)

---

### Post by laurenipsum on 2008-09-28
Thank you so much!

Okay, so far the only suggestion I've tried is to use the Live CD to investigate my partitions. This is what I got:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1c861c85

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5100    40965718+   7  HPFS/NTFS
/dev/sda2            6388        7662    10241437+  83  Linux
/dev/sda3            7663       18176    84453673+   f  W95 Ext'd (LBA)
Partition 3 does not end on cylinder boundary.
/dev/sda5            7663       14046    51279448+   7  HPFS/NTFS
/dev/sda6           14047       18176    33174193+   7  HPFS/NTFS

```

I recognize all the partitions except for SDA3. I now know where my Linux files are and I can migrate them, but now I'm worried about my Fat32 partition, which has apparently disappeared. Or did it merge with other "uncreated" partitions to become sda3? 

I tried mounting sda3, and got "you must specify the filesystem type." I tried editing the fstab file but I don't really know what I'm doing anymore LOL.

---

### Post by caljohnsmith on 2008-09-28
So you are currently able to get the Grub menu on start up, but when you choose Ubuntu, it doesn't boot? If that is true, then most likely all you need to do is change your Grub's menu.lst (assuming your partitions are OK). Try the following from the Live CD and post the output:
```
sudo mount /dev/sda2 /mnt
cat /mnt/boot/grub/menu.lst
```
By the way, I don't know what happened to your FAT32 partition, but it doesn't seem to be there according to both Partition Logic and fdisk.

---

### Post by laurenipsum on 2008-09-28
Actually, I no longer access GRUB at startup. Since I reinstalled Win XP, it boots straight to Windows. I just reboot when I access the Live CD. 

Will check with what you gave me in a few. Thanks!

> By the way, I don't know what happened to your FAT32 partition, but it doesn't seem to be there according to both Partition Logic and fdisk.

Wait...WHAT? *panic* Isn't there a way to find out if it's still there? Somehow? In some...form?

---

### Post by laurenipsum on 2008-09-28
Oh, wait, I forgot. I already got to mount sda2 (and all the other partitions) except for sda3. I already got my files from Linux. Main problem now is how to find that FAT32 one. :confused:

---

### Post by caljohnsmith on 2008-09-28
OK, well first to put Grub back into the MBR (master boot record), you can do the following from a Live CD:
```
sudo grub
grub> find /boot/grub/stage1
```
The above command should return your Ubuntu partition as (hd0,1), if it does, continue:
```

grub> root (hd0,1)
grub> setup (hd0)
grub> quit
```
Also, please post the output of the commands I gave in my last post so I can look at your menu.lst.

---

### Post by TeXtonyx on 2008-09-28
"but now I'm worried about my Fat32 partition, which has apparently disappeared. Or did it merge with other "uncreated" partitions to become sda3?"
When you boot to XP, did you use My Computer to see if you have a fat32 disk?
Also if you have Administrative Tools installed, you can check with Control Panel ->
Administrative Tools -> Computer Management -> Disk Management
I don't know if fixing that cylinder boundary error will provide more information.
mount -t vfat /dev/sda? /mnt  , cd /mnt, ls , lets you view your fat32 folder if you have one.

---

### Post by laurenipsum on 2008-09-29
caljohnsmith, this is what I got. 

```
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt
ubuntu@ubuntu:~$ cat /mnt/boot/grub/menu.lst
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
# kopt=root=UUID=61889bf6-eb00-4312-89b8-2a7ccc453908 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=61889bf6-eb00-4312-89b8-2a7ccc453908 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=61889bf6-eb00-4312-89b8-2a7ccc453908 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

ubuntu@ubuntu:~$ 

```

---

### Post by laurenipsum on 2008-09-29
After following [this set of instructions]("http://ubuntuforums.org/showpost.php?p=5871141&postcount=7"), this line appeared: "Probing devices to guess BIOS drives. This may take a long time." I guess this means it was successful? Should I do [FONT="Courier New"]sudo mount /dev/sda2 /mnt[/FONT] and 
[FONT="Courier New"]cat /mnt/boot/grub/menu.lst[/FONT] again?

---

### Post by laurenipsum on 2008-09-29
TeXtonyx - yes, I use My Computer to view the partitions. No manifestation whatsoever of the fat 32. I will try looking at the admin tools as soon as I reboot. But how do I fix the cylinder boundary error?

> mount -t vfat /mount -t vfat /dev/sda? /mnt  , cd /mnt, lsdev/sda? /mnt  , cd /mnt, ls , lets you view your fat32 folder if you have one.

I already tried one of these. Posting the results here.
```
ubuntu@ubuntu:~$ sudo mount -t vfat /dev/sda3 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
ubuntu@ubuntu:~$ 
```

I tried lsdev /sda3 and this long list appeared. I don't know what I'm looking for. Are the results from this relevant? Should I post it?

---

### Post by laurenipsum on 2008-09-29
Yay! Sort of. GRUB returned, but when I attempted to load any of the Linux modes (memtest, recovery), I got "Error 17: Cannot mount selected partition."

In Windows, I looked up Disk Management, and they're there! Somehow. [**_Here's a screenshot_**]("http://i537.photobucket.com/albums/ff333/laurenipsum/Forums/diskmanagementscreenshot.jpg?t=1222668050"). There are 3 extra partitions of about 9 gigs each, two of them "Unallocated" and one diagnosed "Healthy (Unknown partition)." 

Oh no. I fear the "healthy" one is Linux, and my fat 32 drive has become "unallocated."

The only option for the "healthy" one is to delete it, while the unallocated ones allow me to create a partition (duh). Oh noes. [-o<

---

### Post by TeXtonyx on 2008-09-29
Your original post described F: as your fat32 partition "F. FAT32 partition - about 10 gigs"
which is the size of the unallocated space, 9.81 GB. after the E: Projects partition. If that
was your fat32 partition, the 9.81 GB unallocated, then it would have been labeled F.
I don't make all my partitions the same size, I think it is better to make a 9, 10 and 11, so
you can tell what is there just by the partition size. I choose 'use the largest unallocated
space' when installing Ubuntu and I wouldn't have two partition of nearly equal size in 
unallocated space, Ubuntu might make a mistake. Some software has an option of restore
a deleted partition. But I don't have a reliable partition restore or recover deleted files
software to recommend, this much time after the fact.

---

### Post by caljohnsmith on 2008-09-29
Laurenipsum, try rebooting, and when you get the Grub menu, select the first Ubuntu entry, hit "e" to edit it, select the line that says "root (hd0,2)", press "e" to edit it, change it to "root (hd0,1)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to boot into Ubuntu. Note that the above change is not permanent, so once you boot into Ubuntu, you will need to modify your menu.lst to make the change permanent:
```
gksudo gedit /boot/grub/menu.lst
```
Then copy/paste the following menu.lst over your old one (the changes are highlighted):
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
# kopt=root=UUID=61889bf6-eb00-4312-89b8-2a7ccc453908 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
[COLOR="Red"]# groot=(hd0,1)
[/COLOR]
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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		[COLOR="Red"](hd0,1)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=61889bf6-eb00-4312-89b8-2a7ccc453908 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		[COLOR="Red"](hd0,1)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=61889bf6-eb00-4312-89b8-2a7ccc453908 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		[COLOR="Red"](hd0,1)[/COLOR]
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```
Save, reboot, and you should be able to boot into Ubuntu with no problem now. Let me know how it goes.

---

### Post by laurenipsum on 2008-10-07
Thank you, everyone, for your help. The problem is beyond repair, unfortunately. For a time I was actually able to dual-boot again, but one of my relatives went and fiddled with the partitions, and now all but one disappeared. 

I'm now trying to manually recover all my files. Looks possible, but it'll probably take a few days to get everything. *sigh* Moral of the story: backup is your friend. :D 

Again, thank you for your help.:D

---

### Post by caljohnsmith on 2008-10-07
Laurenipsum, just thought I would mention that two great programs for recovering partitions/files are testdisk and [photorec]("http://www.cgsecurity.org/wiki/PhotoRec"), respectively. Both come in the same package, and you can download them with:
```
sudo apt-get install testdisk
```
If you want any help using them, let me know. Otherwise, best of luck with your data recovery (however you are doing it) and hope you can recover your important files. :)

---

