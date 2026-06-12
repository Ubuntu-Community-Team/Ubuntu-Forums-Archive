---
title: "Cannot install GRUB at all"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by Levan666 on 2009-04-23
Hello,
I realise this is quite a common problem however, i have thoroughly searched and used all the guides i have found to reinstall grub yet i cannot. The furthest i have gotten is by following this guide [http://ubuntuforums.org/showthread.php?t=922678 ]("http://ubuntuforums.org/showthread.php?t=922678http://ubuntuforums.org/showthread.php?t=922678")and that got me an error 2 at the GRUB Inisializing page. 

The full story is, i reinstalled Windows XP which obviously got rid of the GRUB MBR, i rebooted into a livecd to restore it.
I typed:
```
Sudo Grub
find /boot/grub/stage1
```
and it came up with file not found.
With the command fdisk -l, it is shown that the boot partition is sda3 which is the windows partition, sda1 is the ubuntu and sda2 is the swap. I can post full output if it helps.

I can't go anywhere from this and would greatly appreciate any help that could be given.

---

### Post by Mark Phelps on 2009-04-23
I know this is nitpicking, but the way you posted the command it won't work.  You need to do "sudo grub" not "Sudo Grub".

Also, after you do the grub command, do you get the "grub>:" prompt?

---

### Post by Levan666 on 2009-04-24
Sorry, yes, it was unceccecary capitilisation. I did the sudo grub and it did give me the grub> prompt.

---

### Post by meierfra. on 2009-04-24
Try

```
sudo grub
find /grub/stage1
find /stage1
```


If both of the "find" commands return "file not found"   and download the Boot Info Script to the desktop of the Ubuntu Live CD:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and type:


```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post (use the code tags)

---

### Post by Levan666 on 2009-04-24
Unfortunately those commands did not work, here is the result.txt:
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda1 and looks 
                       at sector 201949247 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x406848f1

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   484,472,204   484,472,142  83 Linux
/dev/sda2         484,472,205   489,388,094     4,915,890  82 Linux swap / Solaris
/dev/sda3    *    489,388,095   976,751,999   487,363,905   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="1b2065ad-8bff-4ff2-99b0-122b3ec92de7" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="740a1cd7-f3d9-4710-9601-b7d204a7ae6e" TYPE="swap" 
/dev/sda3: UUID="88C0AEF3C0AEE722" TYPE="ntfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)


=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=1b2065ad-8bff-4ff2-99b0-122b3ec92de7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1b2065ad-8bff-4ff2-99b0-122b3ec92de7

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
# defoptions=quiet splash vga=791

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

title		Ubuntu Intrepid Ibex (8.10)
uuid		1b2065ad-8bff-4ff2-99b0-122b3ec92de7
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=1b2065ad-8bff-4ff2-99b0-122b3ec92de7 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows 7
root		(hd0,2)
savedefault
makeactive
chainloader	+1


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=1b2065ad-8bff-4ff2-99b0-122b3ec92de7 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda2 :
UUID=740a1cd7-f3d9-4710-9601-b7d204a7ae6e none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda3 /media/Windows ntfs-3g defaults,locale=en_AU.UTF-8 0 0

=================== sda1: Location of files loaded by Grub: ===================


 103.3GB: boot/grub/menu.lst
 112.8GB: boot/grub/stage2
 103.4GB: boot/initrd.img-2.6.27-11-generic
 103.3GB: boot/initrd.img-2.6.27-7-generic
 103.4GB: boot/vmlinuz-2.6.27-11-generic
 103.3GB: boot/vmlinuz-2.6.27-7-generic
 103.4GB: initrd.img
 103.3GB: initrd.img.old
 103.4GB: vmlinuz
 103.3GB: vmlinuz.old

================================ sda3/boot.ini: ================================

[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```

---

### Post by meierfra. on 2009-04-24
Try this in a terminal in the LiveCD:


```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt --recheck /dev/sda
```


Post the output of whose commands, reboot and hope for the best.

---

### Post by Levan666 on 2009-04-24
here is the output:
```
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt --recheck /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Unknown partition table signature
Unknown partition table signature
Unknown partition table signature
Unknown partition table signature
Unknown partition table signature
Unknown partition table signature
The file /mnt/boot/grub/stage1 not read correctly.

```

and still no grub upon reboot :(

---

### Post by meierfra. on 2009-04-24
This won't cure  your problem, but while I'm trying to figure out what to do next, could you post the output of:

```
sudo  mount /dev/sda1 /mnt
ls -l /mnt/boot/grub
ls -l /usr/lib/grub/i386-pc  

```

---

### Post by meierfra. on 2009-04-24
After you posted the output I requested in my last post, download the attached file stage1.txt to the Desktop of your LiveCD. Then

```
sudo mount /dev/sda1 /mnt  (ignore any "is already mounted message")
cd /mnt/boot/grub
sudo mv stage1 stage1.bu
sudo cp ~/Desktop/stage1.txt stage1
sudo grub
```

and at the  "grub>" prompt

```
root (hd0,0)
setup (hd0)
quit
```

Before you type "quit" post the content of the terminal. Reboot and report what happened.

---

### Post by Levan666 on 2009-04-24
Thank you very much for helping, i greatly appreciate it.

```
ubuntu@ubuntu:~$ sudo  mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ ls -l /mnt/boot/grub
total 224
-rw-r--r-- 1 root root    197 2009-04-25 07:30 default
-rw-r--r-- 1 root root     45 2009-04-25 07:30 device.map
-rw-r--r-- 1 root root   8660 2009-04-25 07:30 e2fs_stage1_5
-rw-r--r-- 1 root root   8452 2009-04-25 07:30 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-02-25 04:59 installed-version
-rw-r--r-- 1 root root   9152 2009-04-25 07:30 jfs_stage1_5
-rw-r--r-- 1 root root   4241 2009-04-22 08:04 menu.lst
-rw-r--r-- 1 root root   4241 2009-04-22 08:04 menu.lst~
-rw-r--r-- 1 root root   4257 2009-04-10 11:49 menu.lst.backup
-rw-r--r-- 1 root root   7860 2009-04-25 07:30 minix_stage1_5
-rw-r--r-- 1 root root  10132 2009-04-25 07:30 reiserfs_stage1_5
drwxr-xr-x 2 root root   4096 2009-04-10 11:49 splashimages
-rw-r--r-- 1 root root    512 2009-04-25 07:30 stage1
-rw-r--r-- 1 root root 110292 2009-04-25 07:30 stage2
-rw-r--r-- 1 root root   9980 2009-04-25 07:30 xfs_stage1_5
ubuntu@ubuntu:~$ ls -l /usr/lib/grub/i386-pc  
total 271
-rw-r--r-- 1 root root   8660 2007-09-10 21:09 e2fs_stage1_5
-rw-r--r-- 1 root root   8452 2007-09-10 21:09 fat_stage1_5
-rw-r--r-- 1 root root   9152 2007-09-10 21:09 jfs_stage1_5
-rw-r--r-- 1 root root   7860 2007-09-10 21:09 minix_stage1_5
-rw-r--r-- 1 root root  10132 2007-09-10 21:09 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2007-09-10 21:09 stage1
-rw-r--r-- 1 root root 110292 2007-09-10 21:09 stage2
-rw-r--r-- 1 root root 110292 2007-09-10 21:09 stage2_eltorito
-rw-r--r-- 1 root root   9980 2007-09-10 21:09 xfs_stage1_5
ubuntu@ubuntu:~$ hexdump -C
ubuntu@ubuntu:~$

```

The hexdump command didn't do anything for about 10-20 minutes and then it just gave me the ubuntu@ubuntu: prompt again.

---

### Post by meierfra. on 2009-04-24
> the hexdump command didn't do anything for about 10-20 minutes and 

Sorry about that.  I forgot to delete that  command.

The output of the other commands did not reveal any problems.  So I doubt that the instruction from my previous post, will improve the situation. But you might as well give it a try.

---

### Post by Levan666 on 2009-04-24
> **meierfra. said:**
> After you posted the output I requested in my last post, download the attached file stage1.txt to the Desktop of your LiveCD. Then

```
sudo mount /dev/sda1 /mnt  (ignore any "is already mounted message")
cd /mnt/boot/grub
sudo mv stage1 stage1.bu
sudo cp ~/Desktop/stage1.txt stage1
sudo grub
```

and at the  "grub>" prompt

```
root (hd0,0)
setup (hd0)
quit
```

Before you type "quit" post the content of the terminal. Reboot and report what happened.

Still receiving the same error

```
grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 2: Bad file or directory type

```

---

### Post by meierfra. on 2009-04-24
error 2 can be caused by setting in your bios.  Did you have any changes in your bios since you originally installed Ubuntu?

error 2 can also be caused by problems with the filesytem, so lets run a file system check:

```
sudo umount /dev/sda1
sudo e2fsck -fyv /dev/sda1

```

Also undo the commands from my previous post:

```
sudo mount /dev/sda1 /mnt
cd /mnt/boot/grub
sudo mv stage1.bu stage1 
```

and then try to install grub again

```
sudo grub
root (hd0,0)
setup (hd0)
quit
```

---

### Post by Levan666 on 2009-04-24
I think i may have flashed my bios to a more recent version.
I ran the filesystem check but still receiving error 2 when trying to install grub.

---

### Post by meierfra. on 2009-04-24
Let's try one more attempt to install grub:

```
sudo mount /dev/sda1 /mnt
cd /mnt
sudo cp {/,}etc/resolv.conf
sudo mount --bind {/,}proc
sudo mount --bind {/,}sys
sudo mount --bind {/,}dev
sudo chroot /mnt
```

and at the new prompt

```
apt-get purge grub
apt-get install grub
exit
```
Back at the normal prompt:

```
sudo grub-install --root-directory=/mnt --recheck /dev/sda
```

Reboot.  

If this did not work:
 Here are a couple of threads, where people were able to cure  "grub error 2" by changing setting in their bios: (If you do change some settings, make sure to record the original setting)


[http://ubuntuforums.org/showthread.php?t=151682](http://ubuntuforums.org/showthread.php?t=151682)
[http://ubuntuforums.org/showthread.php?t=933239](http://ubuntuforums.org/showthread.php?t=933239)

---

### Post by meierfra. on 2009-04-24
What Live CD are you using?  Ubuntu 8.10?  Or an earlier version?

---

### Post by meierfra. on 2009-04-24
Couple of more options:

1.  Reinstall grub as follows:

```
sudo mount /dev/sda1 /mnt
sudo mount --bind {/,}proc
sudo mount --bind {/,}sys
sudo mount --bind {/,}dev
sudo chroot /mnt
grub 
root (hd0,0)
setup (hd0)
quit
exit
```


2. Get  the SuperGrub CD from [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
After you burned the CD, boot from the CD. 
At the first screen choose 

GRUB => MBR & !LINUX! (1) AUTO ;- )))

For more information see [http://www.supergrubdisk.org/wiki/Howto_Fix_Grub](http://www.supergrubdisk.org/wiki/Howto_Fix_Grub)

---

### Post by Levan666 on 2009-04-24
Sorry for the late reply.
the command
```
ubuntu@ubuntu:/mnt$ sudo grub-install --root-directory=/mnt --recheck /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
The file /mnt/boot/grub/stage1 not read correctly.
```

the part where it said stage1 could not read correctly is what made grub have an error 2, or so i think.

---

### Post by meierfra. on 2009-04-24
Try my suggestions from the last post before you investigate your bios. Maybe the problem is caused by the LiveCD rather than your bios.  If that's the case, installing grub from the "chroot"  or using Super grub  might work.

---

### Post by Levan666 on 2009-04-24
I have tried your alternate method for installing grub and it returned "mount: mount point proc does not exist" for the mount proc, sys and dev commands. Super disk also had an error of some kind. Just to be sure i used a different livecd from a different OS altoghter. I booted up Sabayon V4 and installed grub the simple way


```
grub> find /boot/grub/stage1
 (hd0,0)

grub> root (hd0,0)
 Filesystem type is ext2fs, partition type 0x83

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub> quit
```

This all looked very hopeful, however, when i went to reboot, i still got an error 2.

---

### Post by meierfra. on 2009-04-24
```
"mount: mount point proc does not exist"
```

Oops, that was my fault. I left out a "cd /mnt".  But since  you got grub installed via the  Sabayon V4 CD,  no need  to try this again. 


> i still got an error 2. 

Darn.   I still don't  think its the bios fault. So try this

```
sudo mount /dev/sda1 /mnt
cd /mnt
sudo cp {/,}etc/mtab
sudo mount --bind {/,}proc
sudo mount --bind {/,}sys
sudo mount --bind {/,}dev
sudo chroot /mnt
grub-install /dev/sda

```

---

### Post by Levan666 on 2009-04-24
I am currently using the Sabayon CD as it supports my wireless card so i wont have to move all my stuff down stairs to the router just to connect my laptop to the ethernet port.

The output of your suggested commands:

```
sabayonuser@sabayonx86-64 ~ $ sudo mount /dev/sda1 /mnt
sabayonuser@sabayonx86-64 ~ $ cd /mnt
sabayonuser@sabayonx86-64 /mnt $ sudo cp {/,}etc/mtab
sabayonuser@sabayonx86-64 /mnt $ sudo mount --bind {/,}proc
sabayonuser@sabayonx86-64 /mnt $ sudo mount --bind {/,}sys
sabayonuser@sabayonx86-64 /mnt $ sudo mount --bind {/,}dev
sabayonuser@sabayonx86-64 /mnt $ sudo chroot /mnt
id: cannot find name for group ID 11
id: cannot find name for group ID 409
id: cannot find name for group ID 410
id: cannot find name for group ID 411
root@sabayonx86-64:/# grub-install /dev/sda
You shouldn't call /sbin/grub-install. Please call /usr/sbin/grub-install instead!

Could not find device for /boot: Not found or not a block device.

```

This is very strange. If the windows MBR can be reinstalled in one simple command, GRUB should be able to aswell, i wonder whats gotten into my computer

---

### Post by meierfra. on 2009-04-24
> sabayonx86-64 

Is your ubuntu install 32 bit or 64 bit?  One cannot chroot from  64bit LiveCD  to a 32 bit installation.

Anyway, I'm out of time for today, but will check back in tomorrow. 

In the mean time, you might check out  the two threads concerning the bios,

---

### Post by Levan666 on 2009-04-25
My computer is definitley a 32bit computer and im quite positve the Sabayon cd was also 32bit. 

Some extra information that may be of relevance or may help is that the current installation of Ubuntu is 8.10, the live CD i was using was 7.10 along with Sabayon Four Oh (4.0)

---

### Post by meierfra. on 2009-04-25
> My computer is definitley a 32bit computer and im quite positve the Sabayon cd was also 32bit.

Some extra information that may be of relevance or may help is that the current installation of Ubuntu is 8.10, the live CD i was using was 7.10 along with Sabayon Four Oh (4.0)

O.K   I think some of your problems might have been  caused by the 7.10 LiveCD. But  using the 7.10 LiveCD should be ok, as long as we run all the relevant commands from a  chroot.  So lets try one more time to reinstall grub.
Boot from the Ubuntu 7.10 LiveCD

```
sudo mount /dev/sda1 /mnt
cd /mnt
sudo cp {/,}etc/resolv.conf
sudo mount --bind {/,}proc
sudo mount --bind {/,}sys
sudo mount --bind {/,}dev
sudo chroot /mnt
```

and at the new prompt

```

apt-get purge grub
apt-get install grub
grep -v rootfs /proc/mounts> /etc/mtab
grub-install  --recheck /dev/sda

```

Post the whole content of the terminal.

```
exit
```

Post the whole content of the terminal.

Then reboot and let me know  exactly what happens when you try to boot into Ubuntu.

---

### Post by Levan666 on 2009-04-25
It worked!!!!
Thank you so much!!
Rebooted into grub with no problems and booted up Ubuntu without a hitch.

Once again, thank you so much!!:):):):)

---

### Post by meierfra. on 2009-04-25
> It worked!!!!
Great. Sorry that it took me so long to figure out the correct commands to reinstall grub, but both of your LiveCDs seem to have problems  with your Ubuntu installation.

Have fun with Jaunty and XP.

---

