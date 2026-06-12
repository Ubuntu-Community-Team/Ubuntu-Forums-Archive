---
title: "Install Breaks MBR?"
date: 2009-07-08
forum: Installation &amp; Upgrades
---

### Post by joeyknuccione on 2009-07-08
I did a clean install of Jaunty on my partitioned hard drive, and now I get the "no operating system" error, or the "error 15" error. My SuperGrub disk can't even fix it. The only way I can work now is through the live CD.

Some info:

sudo fdisk -l:
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003c5c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6223    49986216    5  Extended
/dev/sda3            6224       18900   101828002+  83  Linux
/dev/sda4           18901       19457     4474102+  82  Linux swap / Solaris
/dev/sda5   *           1        6223    49986184+  83  Linux

```
and:

grub> find /media/disk/boot/grub/stage1
```

Error 15: File not found

```
^ That was after I followed another thread about restoring grub. I did the setup and used (hd0) with the other part as (hd0,4), per a previous grub request that said grub was on hd0,4.

---

### Post by merlinus on 2009-07-08
What is on sda3?

---

### Post by joeyknuccione on 2009-07-08
> **merlinus said:**
> What is on sda3?

Thanks for your reply.

sda3 is my "storage" drive. Here's what GParted says:

```

/dev/sda1 extend 47.67GiB
   /dev/sda5 ext3 /media/disk 47.67 GiB <this should be my Jaunty install
/dev/sda3 ext3 <this is my "storage"
/dev/sda4 linux-swap <obviously my swap, but I think this is where my grub got installed from a previous manual attempt

```

---

### Post by merlinus on 2009-07-08
If sda5 is your 9.04 install, then the mountpoint should be /, not /media/disk.  From what I see, you do not have a / directory, so I wonder how you managed to install without it?

Unless you have manually mounted the partition, of course!

What were the exact grub commands you tried?

---

### Post by joeyknuccione on 2009-07-08
> **merlinus said:**
> If sda5 is your 9.04 install, then the mountpoint should be /, not /media/disk.  From what I see, you do not have a / directory, so I wonder how you managed to install without it?

Unless you have manually mounted the partition, of course!

What were the exact grub commands you tried?
I followed the directions here:

[http://ubuntuforums.org/showthread.php?t=1206803&highlight=error+15&page=2](http://ubuntuforums.org/showthread.php?t=1206803&highlight=error+15&page=2)

see post 11

---

### Post by merlinus on 2009-07-08
So you entered
```
sudo grub
root (hd0,4)
setup (hd0)
quit
```

---

### Post by joeyknuccione on 2009-07-08
> **merlinus said:**
> So you entered
```
sudo grub
root (hd0,4)
setup (hd0)
quit
```
Correct. Of course I had doubts about that "4", because I thought that was my swap space, but I did as the commands told me.

I had previously setup hda5 with the / folder.

---

### Post by merlinus on 2009-07-08
Numbering for these things starts at 0 (zero), so sda5 translates to (hd0,4).  The grub commands you entered are correct, given your setup, but perhaps the problems lie in that the first partition on your hdd is extended, with / within that, and the rest are primaries, but occur later on the disk.

In general, primaries come first, then an extended containing logicals.

With your / partition mounted, post
```

cat /boot/grub/menu.lst
```

You may have to use
```

cat /media/disk/boot/grub/menu.lst
```

---

### Post by joeyknuccione on 2009-07-08
> **merlinus said:**
> Numbering for these things starts at 0 (zero), so sda5 translates to (hd0,4).  The grub commands you entered are correct, given your setup, but perhaps the problems lie in that the first partition on your hdd is extended, with / within that, and the rest are primaries, but occur later on the disk.

In general, primaries come first, then an extended containing logicals.

With your / partition mounted, post
```

cat /boot/grub/menu.lst
```

You may have to use
```

cat /media/disk/boot/grub/menu.lst
```

Sorry if this is too much info, but here's what I get with ../media/disk...

[code]
ubuntu@ubuntu:~$ cat /media/disk/boot/grub/menu.lst
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
# kopt=root=UUID=2b3acc87-f2be-4a5c-be4a-e5de21313b48 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2b3acc87-f2be-4a5c-be4a-e5de21313b48

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
uuid		2b3acc87-f2be-4a5c-be4a-e5de21313b48
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=2b3acc87-f2be-4a5c-be4a-e5de21313b48 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		2b3acc87-f2be-4a5c-be4a-e5de21313b48
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=2b3acc87-f2be-4a5c-be4a-e5de21313b48 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		2b3acc87-f2be-4a5c-be4a-e5de21313b48
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
[/quote]

---

### Post by merlinus on 2009-07-08
Post results of

```
sudo blkid
df -h
```

---

### Post by joeyknuccione on 2009-07-08
> **merlinus said:**
> Post results of

```
sudo blkid
df -h
```

I 'preciate your help!

sudo blkid:
```

/dev/loop0: TYPE="squashfs" 
/dev/sda3: UUID="d4629895-d7d2-4abd-a2b2-91a4a4577291" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="020d9e5a-f896-4ff6-8176-9c881993b53d" TYPE="swap" 
/dev/sda5: UUID="2b3acc87-f2be-4a5c-be4a-e5de21313b48" TYPE="ext3"

```

df -h:
```

Filesystem            Size  Used Avail Use% Mounted on
tmpfs                1007M  2.4M 1004M   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                1007M  2.4M 1004M   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                1007M     0 1007M   0% /lib/init/rw
varrun               1007M  108K 1006M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M  152K 1006M   1% /dev
tmpfs                1007M  116K 1006M   1% /dev/shm
rootfs               1007M   63M  944M   7% /
/dev/sr0              4.3G  4.3G     0 100% /cdrom
/dev/loop0            1.5G  1.5G     0 100% /rofs
tmpfs                1007M   12K 1007M   1% /tmp
/dev/sda5              47G  2.4G   43G   6% /media/disk

```
Wish I could help with info, but I'm a noob.

---

### Post by merlinus on 2009-07-08
[FONT=monospace]It all matches up, so the only conclusion is that, as I said a bit earlier, there is something about the first partition being extended and then two primaries later on in the hdd that may be causing the problem.

If you can back up important data, then perhaps the best solution is to begin fresh.  Install / into a primary partition that is first on your hdd, then create an extended partition with two logicals, one for /home and one for /swap.

That will almost assuredly resolve the booting problem, unless there is something amiss with your hdd.
[/FONT]

---

### Post by joeyknuccione on 2009-07-08
> **merlinus said:**
> [FONT=monospace]It all matches up, so the only conclusion is that, as I said a bit earlier, there is something about the first partition being extended and then three primaries later on in the hdd that may be causing the problem.

If you can back up important data, then perhaps the best solution is to begin fresh.  Install / into a primary partition that is first on your hdd, then create an extended partition with two logicals, one for /home and one for /swap.

That will almost assuredly resolve the booting problem, unless there is something amiss with your hdd.
[/FONT]
Okay, I 'preciate the help. I think I see what you're saying, and I'm going to try to redo the install with a seperate root and home.

Much thanks for your help and I wish you well!

---

### Post by merlinus on 2009-07-08
Good luck, and let us know how it goes.

---

