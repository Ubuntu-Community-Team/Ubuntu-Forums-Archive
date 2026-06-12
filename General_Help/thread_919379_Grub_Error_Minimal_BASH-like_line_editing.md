---
title: "Grub Error: Minimal BASH-like line editing"
date: 2008-09-13
forum: General Help
---

### Post by Kevide on 2008-09-13
I know there are many threads related to this problem, and I apologize for starting yet another on the topic, and again if I have over-looked the appropriate advice, but thus far I am yet to solve my problem. (I am rather new to Linux, I&#8217;m afraid.)

Anyway, my laptop is partitioned between Windows XP and Linux Feisty. When I boot, I receive the following.

> 
Grub loadingstage1.5

[Minimal BASH-like line editing is supported.  For the first word, TAB lists possible command completions.  Anywhere else TAB lists the possible completions of a device/filename.  ] 

I enter in the following:

grub> find /boot/grub/stage2


It returns" (hd0,2)


I enter in: grub> root (hd0,2)

It returns: grub>


I enter grub> setup (hdo)

It returns:

> 
Checking if "/boot/grub/stage1" exists . . . yes
Checking if "/boot/grub/stage2" exists . . . yes
Checking if "/boot/grub/e2fs_stage1_5 (hd0)" . . . 17 sectors are embedded. succeeded
Running "install /boot/grub/stage1 (hd0) (hd0) 1+17 p (hd0,2)/boot/grub/stage2
/boot/grubmenu.lst" . . . succeeded
Done. 

I enter: grub>reboot.

It takes me right back to the "Minimal BASH-like line editing" message.

I appreciate any time any of you give this.

Best.

---

### Post by Pro-reason on 2008-09-14
> **Kevide said:**
> 

I enter grub> setup (hd**o**)


By that, you mean “*setup (hd**0**)*”, right?

---

### Post by caljohnsmith on 2008-09-14
If on start up you get dropped into the Grub command line, it might mean you don't have a menu.lst in your /boot/grub folder in the Ubuntu partition. When you get that Grub command prompt, try the following:
```
grub> find /boot/grub/menu.lst
```
Does that return anything?

---

### Post by Kevide on 2008-09-14
@pro-reason. Yes, merely a typo. Sorry for the confusion.

@caljohnsmith: it returns (hd0,2)

---

### Post by caljohnsmith on 2008-09-14
OK, please boot your Live CD, open a terminal (Applications > Accessories > Terminal), and do:
```
sudo fdisk -lu
```
Post the results of that, and also do:
```
sudo mount /dev/sda3 /mnt
cat /mnt/boot/grub/menu.lst
```
Also, were you ever able to use Grub to boot into Ubuntu? Or did this happen right after a new Ubuntu install? (Please give more details).

---

### Post by Kevide on 2008-09-14
sudo fdisk -lu

Yields:
```
ubuntu@ubuntu:~$ sudo fdisk -lu 

Disk /dev/sda: 80.0 GB, 80026361856 bytes 
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Disk identifier: 0x4b36bdea 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1         8707230    80196479    35744625    7  HPFS/NTFS 
/dev/sda2   *          63     8707229     4353583+   b  W95 FAT32 
/dev/sda3        80196480   153083384    36443452+  83  Linux 
/dev/sda4       153083385   156296384     1606500    5  Extended 
/dev/sda5       153083448   156296384     1606468+  82  Linux swap / Solaris 

```

sudo mount /dev/sda3 /mnt
cat /mnt/boot/grub/menu.lst

Yields:
```
Partition table entries are not in disk order 
ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt 
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your 
# array will desync and will not let you boot your system. 
default         0 

## timeout sec 
# Set a timeout, in SEC seconds, before automatically booting the default entry 
# (normally the first entry defined). 
timeout         10 

## hiddenmenu 
# Hides the menu by default (press ESC to see the menu) 
#hiddenmenu 

# Pretty colours 
#color cyan/blue white/blue 

## password ['--md5'] passwd 
# If used in the first section of a menu file, disable all interactive editing 
```

[hr]

> Also, were you ever able to use Grub to boot into Ubuntu? Or did this happen right after a new Ubuntu install? (Please give more details).

Yes, for a few months after installation, I was able to use grub to choose between Feisty and Windows upon boot.

---

### Post by caljohnsmith on 2008-09-14
If that really is your complete menu.lst, then your menu.lst is the problem; it doesn't have any entries for any OSes. :) Anyway, try this from the Live CD:
```
sudo mount /dev/sda3 /mnt
sudo chroot /mnt
update-grub
cat /boot/grub/menu.lst
```
Please post the output of all the above commands, and then reboot; let me know if you now get the Grub menu where you can choose Windows or Ubuntu, and if you can boot them successfully.

---

### Post by Kevide on 2008-09-14
```


sudo mount /sda3 /mnt
mount:special device /sda3 does not exist

sudot chroot /mnt
chroot: cannot run command 'bin/bash': No such file or directory

update-grub
Searching for GRUB installation directory. . .
No GRUB directory foun. To create a template run 'mkdir /boot/grub' first To install grub, intall it manually or try 'grub-install' comann. ### Warning, grub-install is used to change you MBR ###.

cst /boot/grub/menu.lst
cst:command not found.

```

Still not booting, I'm afraid.

---

### Post by caljohnsmith on 2008-09-14
My mistake in one of my commands--I corrected my previous post. Try running them again and let me know what you get.

---

### Post by Kevide on 2008-09-14
```

To run a command as administrator (user "root"), use "sudo <command>". 
See "man sudo_root" for details. 

ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt 
ubuntu@ubuntu:~$ sudo chroot /mnt 
root@ubuntu:/# update-grub 
Searching for GRUB installation directory ... found: /boot/grub 
findfs: Unable to resolve 'UUID=62d63894-340d-409b-9d2c-971081da7410' 
Cannot determine root device.  Assuming /dev/hda1 
This error is probably caused by an invalid /etc/fstab 
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst 
Searching for splash image ... none found, skipping ... 
Found kernel: /boot/vmlinuz-2.6.20-15-generic 
Found kernel: /boot/memtest86+.bin 
Updating /boot/grub/menu.lst ... done 

root@ubuntu:/# cat /boot/grub/menu.lst 
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your 
# array will desync and will not let you boot your system. 
default         0 

## timeout sec 
# Set a timeout, in SEC seconds, before automatically booting the default entry 
# (normally the first entry defined). 
timeout         10 

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
# title         Windows 95/98/NT/2000 
# root          (hd0,0) 
# makeactive 
# chainloader   +1 
# 
# title         Linux 
# root          (hd0,1) 
# kernel        /vmlinuz root=/dev/hda2 ro 
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
# kopt=root=UUID=62d63894-340d-409b-9d2c-971081da7410 ro 

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

## ## End Default Options ## 

title           Ubuntu, kernel 2.6.20-15-generic 
root            (hd0,2) 
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=62d63894-340d-409b-9d2c-971081da7410 ro quiet splash 
initrd          /boot/initrd.img-2.6.20-15-generic 
quiet 
savedefault 

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode) 
root            (hd0,2) 
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=62d63894-340d-409b-9d2c-971081da7410 ro single 
initrd          /boot/initrd.img-2.6.20-15-generic 

title           Ubuntu, memtest86+ 
root            (hd0,2) 
kernel          /boot/memtest86+.bin 
quiet 

### END DEBIAN AUTOMAGIC KERNELS LIST 

# This is a divider, added to separate the menu items below from the Debian 
# ones. 
title           Other operating systems: 
root 


# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sda1 
title           Microsoft Windows XP Home Edition 
root            (hd0,0) 
savedefault 
makeactive 
chainloader     +1 


# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sda2 
title           Windows NT/2000/XP 
root            (hd0,1) 
savedefault 
makeactive 
chainloader     +1 

root@ubuntu:/# 

```

Upon reboot, it takes me back to the initial grub error.

---

### Post by Pro-reason on 2008-09-14
Everything seems fine to me, so the only thing that could be wrong, as far as I can tell, is this couple of lines: 

```

kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=62d63894-340d-409b-9d2c-971081da7410 ro quiet splash 
initrd          /boot/initrd.img-2.6.20-15-generic 

```
Either that kernel version number is wrong, or that UUID does not correctly refer to the partiton in question.

Personally, my Ubuntu entry looks like this:

```

title		Ubuntu 8.04.1
root		(hd1,6)
kernel		/vmlinuz root=LABEL=Ubuntu ro splash savedefault vga=normal
initrd		/initrd.img
savedefault

```

The correct kernel and the correct initial ramdisk image are referred to by the symlinks &#8220;/vmlinux&#8221; and &#8220;/initrd.img&#8221;.  My root partition is identified by a volume label.

To see a list of partitions with the correct UUID or LABEL for each one, simply type &#8220;sudo blkid&#8221;.

---

### Post by Kevide on 2008-09-15
After entering sudo blkid:

```

/dev/sda2: LABEL="RECOVERY" UUID="5BB3-0C6E" TYPE="vfat"
/dev/sda3: UUID="62d63894-340d-409b-9d2c-971081da7410" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda5: TYPE="swap" UUID=b031b927-7306-4bbf-9ea2-3e6b82e741dd" 
```

---

### Post by Pro-reason on 2008-09-15
> **Kevide said:**
> After entering sudo blkid:

```

/dev/sda2: LABEL="RECOVERY" UUID="5BB3-0C6E" TYPE="vfat"
/dev/sda3: UUID="62d63894-340d-409b-9d2c-971081da7410" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda5: TYPE="swap" UUID=b031b927-7306-4bbf-9ea2-3e6b82e741dd" 
```

The UUID matches the UUID for sda3, so all seems well.

However, I can see a recovery partition (presumably for Windows), but no Windows partition.  That seems pointless.  Delete it.

The next thing to check is the kernel.

---

### Post by Kevide on 2008-09-15
I'm uncertain of how to do that.

---

### Post by caljohnsmith on 2008-09-15
Kevide, from your Live CD, do the following:
```
sudo mount /dev/sda3 /mnt
ls -l /mnt
ls -l /mnt/boot
```
That will let us know what kernels/initrd images you've got.

---

### Post by Kevide on 2008-09-15
```

ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt 
ubuntu@ubuntu:~$ ls -1 /mnt 
bin 
boot 
cdrom 
dev 
etc 
home 
initrd 
initrd.img 
lib 
lost+found 
media 
mnt 
opt 
proc 
root 
sbin 
srv 
sys 
tmp 
usr 
var 
vmlinuz 
ubuntu@ubuntu:~$ ls -1 /mnt/boot 
abi-2.6.20-15-generic 
config-2.6.20-15-generic 
grub 
initrd.img-2.6.20-15-generic 
initrd.img-2.6.20-15-generic.bak 
memtest86+.bin 
System.map-2.6.20-15-generic 
vmlinuz-2.6.20-15-generic 
ubuntu@ubuntu:~$ 

```

---

### Post by caljohnsmith on 2008-09-15
OK, it looks like the kernel and initrd image your menu.lst is using for Ubuntu is fine. What exactly happens on start up now? Do you get the Grub menu where you can choose Ubuntu, or are you being dropped into the Grub command line with the "grub>" prompt? Does Grub return any specific errors?

---

### Post by Kevide on 2008-09-15
```
Grub loadingstage1.5

[Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename. ] 
```

Same as before. :(

---

### Post by caljohnsmith on 2008-09-15
OK, next time on reboot when you get the Grub command line, try the following:
```
grub> cat (hd0,2)/boot/grub/menu.lst
```
Does that show your menu.lst, or does it return an error?

Also, let's check your partition table; boot your Live CD, and do:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Then do "proceed", "n" to search for Vista partitions, hit enter, and select "search!" so it does a deeper search, which could take a while. Please post the output of that screen.

---

### Post by Kevide on 2008-09-15
```
grub> cat (hd0,2)/boot/grub/menu.lst
```
Returns several pages.

```
sudo apt-get install testdisk 
```
Returns "couldn't find package testdisk.

Also, only have XP and feisty. No vista.

---

### Post by caljohnsmith on 2008-09-15
Can you get an internet connection when you run your Live CD? If you can, then use the previous commands I gave to run testdisk once you have an internet connection established. If you can't, then try downloading the [System Rescue CD]("http://www.sysresccd.org") on some other computer, burning it to CD, and you can run testdisk from there.

---

### Post by Kevide on 2008-09-16
...err, I think I'm missing something. If i'm running Linux off the CD, how can load the rescue CD?

---

### Post by Pro-reason on 2008-09-16
> **Kevide said:**
> ...err, I think I'm missing something. If i'm running Linux off the CD, how can load the rescue CD?

Read it again.

---

### Post by Kevide on 2008-09-16
You want me to run the testdisk from my second machine?

---

### Post by caljohnsmith on 2008-09-17
> **Kevide said:**
> You want me to run the testdisk from my second machine?
No, I think you misunderstood. If you can't run testdisk from your Live CD, then download that System Rescue CD I mentioned in my previous post, burn it to CD, and then boot off of it. You can run testdisk from the System Rescue CD.

---

### Post by Kevide on 2008-09-17
Ah, of course. Apologies.

---

### Post by Kevide on 2008-09-18
```
Selected disk does not exist
```

```
 Unrecognized command 
```

---

