---
title: "Grub has mysteriously vanished"
date: 2008-08-14
forum: General Help
---

### Post by OvenMitt Bandit on 2008-08-14
A few weeks ago, I had some problems on my Windows XP partition. After nothing worked, I became discouraged and abandoned the problem. I have been using my Ubuntu 8.04 partition exclusively for about 2 months now. Today, I decided to crack open the problem again. I loaded up XP, made sure the problem was still the same, then popped in an XP install disc to see what I could do. I couldn't find the right option I was looking for in the Windows setup, so I decided to just screw it and reinstall XP. First, I needed to load up Ubuntu to backup some files before I reinstalled. Notice: up to this point, I had done _nothing_. I just looked at the options in the Windows setup and quit out of it. My computer restarted, and loaded straight into XP! No more loading into grub. It has mysteriously disappeared. I have no idea what happened. How do I get my precious grub back?

---

### Post by ThrobbingBrain66 on 2008-08-14
First, boot up your Ubuntu LiveCD, open a terminal and type the following:
```
grub
```
then
```
root (hd0,0)
```
where hd0 is the drive that Ubuntu is on and 0 is the partition.  In this example, it's hard drive 1, partition 1.  (hd0,1) would be hard drive one, partition two.

Then
```
setup (hd0)
```

And finally
```
quit
```

Source: [http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

---

### Post by caljohnsmith on 2008-08-14
I just wanted to add to ThrobbingBrain66's solution an easy way to make sure you get the correct (hdX,Y) partition as it can be easy to mix up. First boot up the Ubuntu Live CD, open a terminal, and then:
```
sudo grub
grub> [COLOR="Blue"]find /boot/grub/stage1[/COLOR]
*[that will find your Ubuntu partition [COLOR="Blue"](hdX,Y)[/COLOR] since it will have Grub's stage1 file]*
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit

```

---

### Post by OvenMitt Bandit on 2008-08-14
When I got to the grub> setup step, I got this back:

```
grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 22: No such partition

```

---

### Post by Howitzer777 on 2008-08-14
Looks like the partition was deleted somehow. are you sure that there was no way you could have accidentally deleted the partition? good thing you backed up your files

---

### Post by caljohnsmith on 2008-08-14
OvenMitt Bandit, can you mount your ubuntu partition? From your Live CD, do the following:```

sudo fdisk -l
```
Find which is your Ubuntu partition in the form sdaX, then mount it:
```
sudo mount /dev/sdaX /mnt
```
Your Grub errored when it was looking for your menu.lst, so see if you have it, and post the contents if you do:
```
cat /mnt/boot/grub/menu.lst
```

---

### Post by OvenMitt Bandit on 2008-08-14
Alrighty, here we go:

```
ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe9ece9ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19699   158232186    7  HPFS/NTFS
/dev/sda2           19700       38913   154336455    5  Extended
/dev/sda3           38726       38913     1510078+  82  Linux swap / Solaris
/dev/sda5           19700       38725   152826282   83  Linux

```

Then:
```
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt

```

Then finally:
```
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
# kopt=root=UUID=c734a99c-90aa-46db-a3ca-dd5859af2aea ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=c734a99c-90aa-46db-a3ca-dd5859af2aea ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=c734a99c-90aa-46db-a3ca-dd5859af2aea ro single
initrd          /boot/initrd.img-2.6.24-19-generic

title           Ubuntu 8.04.1, kernel 2.6.24-18-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-18-generic root=UUID=c734a99c-90aa-46db-a3ca-dd5859af2aea ro quiet splash
initrd          /boot/initrd.img-2.6.24-18-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-18-generic root=UUID=c734a99c-90aa-46db-a3ca-dd5859af2aea ro single
initrd          /boot/initrd.img-2.6.24-18-generic

title           Ubuntu 8.04.1, kernel 2.6.24-17-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-17-generic root=UUID=c734a99c-90aa-46db-a3ca-dd5859af2aea ro quiet splash
initrd          /boot/initrd.img-2.6.24-17-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-17-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-17-generic root=UUID=c734a99c-90aa-46db-a3ca-dd5859af2aea ro single
initrd          /boot/initrd.img-2.6.24-17-generic

title           Ubuntu 8.04.1, kernel 2.6.24-16-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=c734a99c-90aa-46db-a3ca-dd5859af2aea ro quiet splash
initrd          /boot/initrd.img-2.6.24-16-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=c734a99c-90aa-46db-a3ca-dd5859af2aea ro single
initrd          /boot/initrd.img-2.6.24-16-generic

title           Ubuntu 8.04.1, memtest86+
root            (hd0,5)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

---

### Post by caljohnsmith on 2008-08-14
Well for one thing, in your menu.lst your entries for Ubuntu should be (hd0,4) since your Ubuntu partition is sda5. I would go ahead and correct that, and about your setup error in Grub, I would do a file system check on that partition to make sure everything is OK:
```
sudo fsck /dev/sda5
```
Make sure sda5 is not mounted when you run fsck on it. Then go through the previous routine in Grub of doing root ... setup ... etc. and see if it works.

---

### Post by OvenMitt Bandit on 2008-08-14
Alright, I changed the (hd0,5) to (hd0,4) in menu.lst. I then unmounted sda5 and ran fsck:

```
ubuntu@ubuntu:~$ sudo fsck /dev/sda5
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
/dev/sda5: clean, 182340/9551872 files, 2310228/38206570 blocks

```

Went and did the previous root, setup commands, and got the same exact "Error 22: No such partition".

---

### Post by caljohnsmith on 2008-08-15
I think something must have happened to your partitioning, because for one thing notice that your fdisk output says that it is "omitting empty partition" and does not list /dev/sda4. Also, when you had everything working under Grub, you were using (hd0,5) for your Ubuntu menu entries, which would be /dev/sda6. But now your Ubuntu partition appears to be on /dev/sda5 according to fdisk.

Are you sure you didn't do anything with your Windows CD or something else recently that would have changed your partitioning structure? Something definitely seems awry. 

I know you can use "testdisk" to rebuild a corrupt HDD partition table, but I've not actually done it myself since I've never needed to. [Here's a guide]("http://www.users.bigpond.net.au/hermanzone/p21.html") of how you might do it, in case you're interested. But unless you can give more clues, I can't be sure what is really your root problem. If you do decide to rebuild your partition table, I would recommend backing up the one you have now in case your rebuilt one does not fix the problem. That way you can revert to the previous one and have nothing to lose in trying to fix it with testdisk. You can back up your entire MBR, which includes the partition table, with:
```
sudo dd if=/dev/sda of=[COLOR="Blue"]/path/boot.mbr[/COLOR] bs=512 count=1
```
Where the MBR will be saved to /path/boot.mbr. You could run that command from a Live CD and then save the boot.mbr somewhere.

---

### Post by OvenMitt Bandit on 2008-08-15
The only things I did on the Windows disc was load up a recovery console, but I didn't do anything in it. I quit without entering in anything. I also got to the "which partition do you want to set up Windows on?", but I didn't select anything, and quit out of that as well. I do remember seeing my NTFS partition as well as the partition I have Ubuntu on in that list. I did not do _anything_. I have no clue what happened. The Windows setup must have done something without me knowing, which doesn't seem likely, but I can't think of anything else.

As for backing up my MBR, can I back that up to a USB flash drive?

---

### Post by caljohnsmith on 2008-08-15
> **OvenMitt Bandit said:**
> As for backing up my MBR, can I back that up to a USB flash drive?
Sure: you can specify the path to your flash drive with the "of=/path_to_flash_drive/boot.mbr" part of that command.

By the way, I did a quick search on your posts to see if you had ever posted a different fdisk output in the past, and it seems you've had partitioning problems in the past too. Did you ever figure out the root cause of the problems? That could have alot to do with what you are experiencing now.

---

### Post by OvenMitt Bandit on 2008-08-15
Yeah, I had some partitioning problems in the past, but I have a new hard drive now. My previous drive had some physical damage to the disk, causing the problems. Had to get a new drive. Seems like after a few months, my partitioning problems have followed me. :|

Going to back up my MBR, and then run testdisk. I'll report back when I'm done.

EDIT: I have not lost any data, both my Ubuntu and XP partitions are intact. I can mount both and look through the files. My Ubuntu partition wasn't showing up as a drive yesterday, but it is now.

---

### Post by OvenMitt Bandit on 2008-08-15
Alright, I ran testdisk and just had it analyze. This is what it said:

```
Disk /dev/sda - 320 GB / 298 GiB - CHS 38913 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1 19698 254 63  316464372
 2 E extended             19699   0  1 38912 254 63  308672910
 3 P Linux Swap           38725   1  1 38912 254 63    3020157
Space conflict between the following two partitions
 2 E extended             19699   0  1 38912 254 63  308672910
 3 P Linux Swap           38725   1  1 38912 254 63    3020157

```

Space conflict? I don't remember fdisk saying anything about that. Do I need to resolve the conflict before continuing? If so, how?

---

### Post by caljohnsmith on 2008-08-15
The fact that testdisk complains there is a conflict confirms my suspicions that you most likely have a partition problem at this point. It doesn't look like testdisk found your main Ubuntu partition in that initial analysis it did; I would recommend trying the "Recovering a Lost Partition With TestDisk -searching deeper" section of that web page [testdisk guide]("http://www.users.bigpond.net.au/hermanzone/p21.html") I gave earlier.

---

### Post by OvenMitt Bandit on 2008-08-15
Hmm. I need to reinstall XP anyway, do you think it may be easier to just wipe my drive and reinstall both XP and Ubuntu? That way my partitions will get a fresh start.

---

### Post by caljohnsmith on 2008-08-15
> **OvenMitt Bandit said:**
> Hmm. I need to reinstall XP anyway, do you think it may be easier to just wipe my drive and reinstall both XP and Ubuntu? That way my partitions will get a fresh start.
Absolutely. Yes, if you were planning on reinstalling XP anyway, and as long as you've got your personal files backed up, you might save yourself alot of hassle by completely wiping the HDD clean and starting over. So make sure you delete the current partitions with gparted or similar software so you aren't just reinstalling to the same faulty partition structure. And since Win XP always overwrites the MBR when you install, it is much better to install Win XP first and Ubuntu after so that Grub doesn't get overwritten. Good luck.

---

### Post by OvenMitt Bandit on 2008-08-15
Then that's what I'm going to do. Thank you very much for your help, caljohnsmith. :)

---

