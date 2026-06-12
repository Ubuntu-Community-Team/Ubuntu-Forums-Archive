---
title: "Grub Error 2 after Install of 9.04"
date: 2009-05-29
forum: Installation &amp; Upgrades
---

### Post by dbixler on 2009-05-29
I had a previous installation of 8.04, but decided to just delete it and start from scratch.  Installation of the 64bit version when perfectly, but when it rebooted, I got a dreaded Error 2 from Grub, with no options to even attempt to get into a menu.  Here is the results of sudo fdisk -l:

> 
ubuntu@ubuntu:/mnt$ sudo fdisk -l

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xff0470ff

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4253be37

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9000    72292468+   7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000b141

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       59349   476720811   83  Linux
/dev/sdc2           59350       60801    11663190    5  Extended
/dev/sdc5           59350       60801    11663158+  82  Linux swap / Solaris

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
16 heads, 63 sectors/track, 1938021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xebaf2f53

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1     1938018   976761040+   7  HPFS/NTFS



and here's my current menu.lst file:

> 
ubuntu@ubuntu:/mnt$ cat boot/grub/menu.lst 
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
# kopt=root=UUID=8d0fe92f-79d8-433e-9219-99b7acff538f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8d0fe92f-79d8-433e-9219-99b7acff538f

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
uuid		8d0fe92f-79d8-433e-9219-99b7acff538f
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8d0fe92f-79d8-433e-9219-99b7acff538f ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		8d0fe92f-79d8-433e-9219-99b7acff538f
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8d0fe92f-79d8-433e-9219-99b7acff538f ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		8d0fe92f-79d8-433e-9219-99b7acff538f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


Was hoping that someone here might have some suggestions.  I have no IDE drives in my computer, and all IDE devices are disabled in the BIOS.  Any help would be greatly appreciated.

---

### Post by raymondh on 2009-05-29
Hi,

Am posting a thread quite similar.  See lindsay7's post (#3).  It might work ... 

[http://ubuntuforums.org/showthread.php?p=7367369#post7367369](http://ubuntuforums.org/showthread.php?p=7367369#post7367369)

Am thinking GRUB did not update when you upgraded.

Good luck.

---

### Post by dbixler on 2009-05-29
Thanks for the quick response.  Yes, I tried that prior to posting this message but to no avail.  I'm still getting the Error 2.

I wonder if it could have something to do with the fact that I have two drives configured for a RAID0 striping configuration.  Ubuntu 8.04 didn't seem to have any issues with it, in fact, I was able to mount the software RAID0 array in 8.04.

Any other suggestions, or is there any other information I could provide to help debug the situation?

---

### Post by dbixler on 2009-05-29
Oh, and the drive I'm booting from in Ubuntu is NOT on that stripe.  It's the 2nd drive in the system (or 3rd depending on your view).  Basically I have two drives first that make up a single logical drive, and the third drive where I installed Ubuntu.  Booting from the LiveCD shows that drive as /dev/sdc.

---

### Post by raymondh on 2009-05-29
> **dbixler said:**
> Thanks for the quick response.  Yes, I tried that prior to posting this message but to no avail.  I'm still getting the Error 2.

I wonder if it could have something to do with the fact that I have two drives configured for a RAID0 striping configuration. 

I haven't played with RAID hence cannot be sure.  Googling error 2 brings this up:

2 : Bad file or directory type
This error is returned if a file requested is not a regular file, but something like a symbolic link, directory, or FIFO

Are you using fakeraid?  If so, have you seen this page and it's relevance to GRUB mapping?

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

regards,

---

### Post by raymondh on 2009-05-29
When you (in terminal)

```
sudo grub
find /boot/grub/stage1
```

where does it point?

---

### Post by dbixler on 2009-05-29
Thanks for the link.  I think this is related to actually installing onto a software raid drive, which is not what I'm doing.  I may actually go back and try to do a full reinstall using those instructions just to be sure.  However, I'm absolutely positive that the first install did copy the files over.  Is it possible to just FORCE Grub to load the boot image from a particular drive, even if it's just some type of hack?

---

### Post by dbixler on 2009-05-29
> **raymondhenson said:**
> When you (in terminal)

```
sudo grub
find /boot/grub/stage1
```

where does it point?

Let me go reboot and check...

---

### Post by raymondh on 2009-05-29
> **dbixler said:**
> Thanks for the link.  I think this is related to actually installing onto a software raid drive, which is not what I'm doing.  I may actually go back and try to do a full reinstall using those instructions just to be sure.  However, I'm absolutely positive that the first install did copy the files over.  Is it possible to just FORCE Grub to load the boot image from a particular drive, even if it's just some type of hack?

see previous post/question (post 6)

regards,

---

### Post by raymondh on 2009-05-29
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

Regards,

---

### Post by dbixler on 2009-05-29
ubuntu@ubuntu:/mnt$ sudo find . -name stage1 -print
./boot/grub/stage1
./usr/lib/grub/x86_64-pc/stage1

---

### Post by dbixler on 2009-05-29
Oh, and...

```

ubuntu@ubuntu:/mnt$ cat boot/grub/device.map 
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd

```

So it's really hd2 that Ubuntu is installed to.  Maybe I'll try swapping hd0 and hd2 instead of hd1 in the menu.lst file.

---

### Post by raymondh on 2009-05-29
Hi Dbixler,

I'll have to log-out and attend a meeting.  Will recheck thread in about 1 to 1.5 hrs.

good luck,

---

### Post by raymondh on 2009-05-29
> **dbixler said:**
> Oh, and...

```

ubuntu@ubuntu:/mnt$ cat boot/grub/device.map 
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd

```

So it's really hd2 that Ubuntu is installed to.  Maybe I'll try swapping hd0 and hd2 instead of hd1 in the menu.lst file.

Try hd0 first

---

### Post by dbixler on 2009-05-29
Swapping hd0 and hd2 didn't work.  hd0 & hd1, though, should be the software raid drives.  hd2 (which maps to /dev/sdc off of the LiveCD) is where the actual install went to.

---

