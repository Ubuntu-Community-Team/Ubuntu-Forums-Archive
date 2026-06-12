---
title: "Copy installation to a new hard drive"
date: 2008-10-30
forum: General Help
---

### Post by Beloved Bob on 2008-10-30
I have Ubuntu 8.04 on a dual boot with windows. I want to move Ubuntu to an external USB drive. What is the easiest way to do this? Do I use "dd" and if I do, how does it work? Thanks.

---

### Post by skullmunky on 2008-10-30
dd is a very low-level copy program, but I don't think I'd use it for this.  It's best for doing an exact clone, like if you have two identical drives.

I think what I'd do is just do a fresh install on the USB drive and copy any files you need, like your home directory, onto it afterwards.  That would probably be the most -reliable- way.

Another way would be to format the USB drive as ext3 and then copy everything from the existing install onto the USB drive.

The only difficulty you'll have is that you will need to manually edit the /boot/grub/menu.lst file, and probably /etc/fstab as well, so that they have the new drive listed.

---

### Post by Beloved Bob on 2008-10-31
Thanks! I did use dd and it seems to have worked. Now I am in the process of trying to get the grub to work. How would I have to change the /etc/fstab file?

I am new at this...

---

### Post by Beloved Bob on 2008-10-31
I am still looking for help. My dd did not work. How do I format and copy? Would that take care of the boot? Thanks!

---

### Post by caljohnsmith on 2008-10-31
One easy method that I've used that I know works is to simply copy over your entire Ubuntu file system with "cp -ax" from a Live CD; you wouldn't want to do it while you are in the Ubuntu that you want to copy, because then you have to take special steps to omit copying /proc and /sys and special directories like that. 

To do it, just boot your Live CD, and first partition your USB drive with Ubuntu's partition editor (System > Admin > Partition Editor); you'll want at least one ext3 partition for your main install, and you'll probably want a swap partition as well. Any other partitions are up to you. Once the partitions are set up, say your new Ubuntu partition is sdb1 and your old Ubuntu is sda1, then you would do:
```
sudo mkdir /mnt/sda1 /mnt/sdb1
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sdb1 /mnt/sdb1
sudo cp -ax /mnt/sda1/* /mnt/sdb1/.
```
Once you are done copying the files over, you'll need to install Grub to the MBR of your USB drive, modify your menu.lst, modify fstab, and a few other details. See if you can get as far as copying all the files over, and we can work from there. Also post:
```
sudo fdisk -lu
```
So I can know what your partitions are. Let me know how it goes. :)

---

### Post by Beloved Bob on 2008-11-01
Thanks for your help. Copied as you suggested. I am now ready to install GRUB, modify what I need to, and get on with it. Here is the fdisk -lu you want to see:

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x69af68b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   149838254    74919096   83  Linux
/dev/sdb2       149838255   156296384     3229065    5  Extended
/dev/sdb5       149838318   156296384     3229033+  82  Linux swap / Solaris

Thanks, again, for your help. Looking forward to finishing this!

---

### Post by caljohnsmith on 2008-11-02
OK, great, hopefully the copying went as planned. Here's how to install Grub to the MBR of your sdb drive: 
```
sudo grub
grub> device (hd0) /dev/sdb
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
Please post the output of all the above commands. Next, to modify your fstab:
```
sudo mount /dev/sdb1 /mnt
sudo cp /mnt/etc/fstab /mnt/etc/fstab.backup
sudo blkid -c /dev/null
gksudo gedit /mnt/etc/fstab
```
And in your fstab, find the line with the mount point of "/", and use the UUID for sdb1 given by the blkid command above, so it will look similar to:
```
# /dev/sdb1
UUID=[COLOR="Blue"]77677cb5-6e56-4936-a373-80c15de06bca /[/COLOR] ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
```
So replace the UUID with your UUID for sdb1, but you shouldn't need to change any of the options you all ready have after the "ext3" since yours may be entirely different than what's above. Also change the UUID of the swap partition sdb5 in fstab to use the correct UUID given by blkid.

Next open your menu.lst:
```
gksudo gedit /mnt/boot/grub/menu.lst
```
And for all your Ubuntu entries, change the UUID in the kernel line to use your UUID for sdb1, and also make sure the "root" line uses (hd0,0):
```
title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		[COLOR="Red"](hd0,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=[COLOR="Red"]77677cb5-6e56-4936-a373-80c15de06bca[/COLOR] ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```
And make sure you set the "# kopt" line to use the UUID of sdb1:
```
# kopt=root=UUID=[COLOR="Red"]77677cb5-6e56-4936-a373-80c15de06bca[/COLOR] ro
```
And if you had to change the "root" line in the Ubuntu entries to (hd0,0), then also make sure the "# groot" line in that file is:
```
# groot=[COLOR="Red"](hd0,0)[/COLOR]
```

Next open:
```
gksudo gedit /mnt/etc/initramfs-tools/conf.d/resume
```
And change the UUID in that file to be the UUID for your swap partition sdb5. Go ahead and reboot, make sure your BIOS is set to boot the sdb drive, and you should get the Grub menu on start up. When you boot into Ubuntu, you probably won't get a splash screen; so to fix that last detail, once you are in Ubuntu, just run:
```
sudo update-initramfs -u -k all
```
And you should be all set if everything goes well. If you have any problems, let me know, otherwise let me know how it goes. :)

---

### Post by Beloved Bob on 2008-11-02
Hi - Well, I followed as best I could and it did not work. It tries to load and I get "Error 2." 

Here is the output you requested:

Checking if "/boot/grub/stage1" exists... yes 
 Checking if "/boot/grub/stage2" exists... yes 
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes 
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded. 
succeeded 
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,0)/boot/grub/stage2 
/boot/grub/menu.lst"... succeeded 
Done. 

When I tried to edit the fstab file it did not look like the one you provided. Also, my drive letters went from sdb to sda when I removed my hard drive from my computer...wanting to work only with the external USB drive and a live CD.

Suggestions? Perhaps I should format the USB drive and start again? I do not know how to format a drive in Ubuntu...but will follow directions. 

One question: I booted with a live disk and then cd to "/media/disk/" as my root. Is this wrong? I do not know how to work on the USB disk any other way.

Thanks, again, for your help. It is greatly appreciated.

---

### Post by caljohnsmith on 2008-11-02
OK, to begin with, how about first posting the following, assuming the HDD is hooked up and the USB drive is sdb:
```
sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump
sudo mount /dev/sdb1 /mnt
ls -l /mnt
cat /mnt/boot/grub/menu.lst
cat /mnt/etc/fstab
```

---

### Post by Beloved Bob on 2008-11-02
Here is the post:

bob@bob-laptop:~$ cd /media/disk
bob@bob-laptop:/media/disk$ sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB 
bob@bob-laptop:/media/disk$ sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump
0000000 ff00                                   
0000002
bob@bob-laptop:/media/disk$ sudo mount /dev/sdb1 /mnt
bob@bob-laptop:/media/disk$ ls -l /mnt
total 96
drwxr-xr-x   2 root root  4096 2008-10-08 09:21 bin
drwxr-xr-x   3 root root  4096 2008-10-28 08:15 boot
lrwxrwxrwx   1 root root    11 2008-11-01 18:08 cdrom -> media/cdrom
drwxr-xr-x   4 root root  4096 2008-05-01 14:16 dev
drwxr-xr-x 132 root root 12288 2008-11-02 11:05 etc
drwxr-xr-x   4 root root  4096 2008-05-12 14:54 home
drwxr-xr-x   2 root root  4096 2007-10-15 19:17 initrd
lrwxrwxrwx   1 root root    33 2008-11-01 18:13 initrd.img -> boot/initrd.img-2.6.24-21-generic
lrwxrwxrwx   1 root root    33 2008-11-01 18:13 initrd.img.old -> boot/initrd.img-2.6.24-20-generic
drwxr-xr-x  17 root root  4096 2008-10-15 07:15 lib
drwx------   2 root root 16384 2008-04-10 13:58 lost+found
drwxr-xr-x  10 root root  4096 2008-11-01 21:11 media
drwxr-xr-x   2 root root  4096 2007-10-08 06:47 mnt
drwxr-xr-x   7 root root  4096 2008-10-27 17:40 opt
drwxr-xr-x   2 root root  4096 2007-10-08 06:47 proc
drwxr-xr-x  17 root root  4096 2008-10-30 19:25 root
drwxr-xr-x   2 root root  4096 2008-10-15 07:17 sbin
drwxr-xr-x   2 root root  4096 2007-10-15 19:17 srv
drwxr-xr-x   2 root root  4096 2007-10-04 07:17 sys
drwxrwxrwt  13 root root  4096 2008-11-01 21:47 tmp
drwxr-xr-x  12 root root  4096 2008-05-01 13:51 usr
drwxr-xr-x  15 root root  4096 2007-10-15 19:31 var
lrwxrwxrwx   1 root root    30 2008-11-01 18:25 vmlinuz -> boot/vmlinuz-2.6.24-21-generic
lrwxrwxrwx   1 root root    30 2008-11-01 18:25 vmlinuz.old -> boot/vmlinuz-2.6.24-20-generic
bob@bob-laptop:/media/disk$ cat /mnt/boot/grub/menu.lst
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
# kopt=root=UUID=491b6b69-4256-4f29-8c4e-9f34b11cb6d6 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
# howmany=1

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

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=491b6b69-4256-4f29-8c4e-9f34b11cb6d6 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=491b6b69-4256-4f29-8c4e-9f34b11cb6d6 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title		Microsoft Windows XP Embedded
root		(hd0,4)
savedefault
makeactive
chainloader	+1

bob@bob-laptop:/media/disk$ cat /mnt/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=491b6b69-4256-4f29-8c4e-9f34b11cb6d6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=07D7-0A17  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=EACE3EFFCE3EC39B /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=BE6A429C6A4250F7 /media/sda3     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=BA46-803B  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=25D6A7D83B5A13C6 /media/sda7     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda8
UUID=2602C1A31F62196C /media/sda8     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda9
UUID=5aece92b-a687-442e-b6c2-0f3a20afd1e0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
bob@bob-laptop:/media/disk$ 

Hope it makes sense to you...

And in case I did not say it...Thankyou!!!

---

### Post by caljohnsmith on 2008-11-02
> **Beloved Bob said:**
> And in case I did not say it...Thankyou!!!
You're most welcome, and I hope we can get it working for your sake. :) According to those dd commands you ran, it looks like Grub is correctly installed to the USB sdb drive, so it's not a good sign you got a Grub error 2 on start up before even getting a Grub menu. You said you were using Ubuntu 8.04, correct? Just one more sanity check:
```
sudo dumpe2fs /dev/sdb1 | grep -i "inode size"
```
If that command returns "128", then I think it's likely you have a problem with your USB drive settings in BIOS. Try going into your BIOS and look for settings related to HDDs or USB, such as "auto-detect", LBA, CHS, RAID, AHCI vs. IDE, ACPI, DMA, etc. Try changing them one at a time, reboot your USB drive, and see if anything changes. I would recommend writing down whichever settings you change so you can always revert back to the original settings if necessary. Let me know how it goes. :)

---

### Post by Beloved Bob on 2008-11-02
It did not return what you were looking for...

Here it is:

bob@bob-laptop:~$ cd /media/disk
bob@bob-laptop:/media/disk$ sudo dumpe2fs /dev/sdb1 | grep -i "inode size"
[sudo] password for bob: 
dumpe2fs 1.40.8 (13-Mar-2008)
Inode size:		  256
bob@bob-laptop:/media/disk$ 

Any suggestions?

Thanks!

---

### Post by caljohnsmith on 2008-11-02
> **Beloved Bob said:**
> 
```
bob@bob-laptop:/media/disk$ sudo dumpe2fs /dev/sdb1 | grep -i "inode size"
[sudo] password for bob: 
dumpe2fs 1.40.8 (13-Mar-2008)
[COLOR="Red"]Inode size:		  256[/COLOR]
bob@bob-laptop:/media/disk
```$ 

OK, that most likely explains your Grub error 2; did you format the partitions on your sdb drive with the Intrepid Live CD? Some how your sdb ext3 partition was formatted to use the newer 256 byte inode size rather than the older 128 byte inode size that Hardy and previous versions use. That's most likely what is causing Grub to choke right now, because you need the Intrepid version of Grub to handle the 256 byte inode size partitions. 

To fix it, how about downloading the Intrepid grub 0.97-29ubuntu45 package to your desktop from packages.ubuntu.com, and then do the following (if any of the commands return an error, stop immediately and don't continue):
```
cd ~/Desktop
mkdir New_grub
dpkg-deb -x grub*.deb New_grub
sudo mount /dev/sdb1 /mnt
sudo cp New_grub/usr/lib/grub/i386-pc/e2fs_stage1_5 New_grub/usr/lib/grub/i386-pc/stage2 /mnt/boot/grub/.
sudo grub
grub> root (hd1,0)
grub> setup (hd1)
grub> quit
```
Please post the output of all the above commands, reboot, and let me know what happens. :)

---

### Post by Beloved Bob on 2008-11-02
It worked!!! I am so sorry that I did not mention I had used an Intrepid live CD that I have. My apologies. 

It is working wonderfully...below is the post of the final info from the terminal:

bob@bob-laptop:~$ cd ~/Desktop
bob@bob-laptop:~/Desktop$ mkdir New_grub
bob@bob-laptop:~/Desktop$ dpkg-deb -x grub*.deb New_grub
bob@bob-laptop:~/Desktop$ sudo mount /dev/sdb1 /mnt
[sudo] password for bob: 
bob@bob-laptop:~/Desktop$ sudo cp New_grub/usr/lib/grub/i386-pc/e2fs_stage1_5 New_grub/usr/lib/grub/i386-pc/stage2 /mnt/boot/grub/.
bob@bob-laptop:~/Desktop$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.
bob@bob-laptop:~/Desktop$ 

I cannot thank you enough. You were a great help. Someone needs to "buy you a beer" as the saying goes to tell someone they are appreciated. My wife is delighted it is working and I can return to do her "honey-do" list!

THANK YOU! - Bob

---

### Post by caljohnsmith on 2008-11-02
> **Beloved Bob said:**
> 
I cannot thank you enough. You were a great help. Someone needs to "buy you a beer" as the saying goes to tell someone they are appreciated. My wife is delighted it is working and I can return to do her "honey-do" list!

THANK YOU! - Bob
Your most welcome, Bob; I'm really glad it's finally working. Maybe your "honey-do" list will include some things more fun than fixing Ubuntu installs I hope. Anyway, cheers and have fun with Ubuntu. :)

---

