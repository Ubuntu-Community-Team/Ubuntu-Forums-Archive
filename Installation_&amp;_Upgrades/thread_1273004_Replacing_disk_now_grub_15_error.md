---
title: "Replacing disk now grub 15 error"
date: 2009-09-22
forum: Installation &amp; Upgrades
---

### Post by SimonT on 2009-09-22
I have a dual boot system windows xp and Ubuntu, My disk had a few bad block and was also quite small.

I cloned my disk on to a bigger larger disk but when I changed out the disk my grub loader came up with error 15

This is what my disks look like when both are connected 
(in windows)

[[IMG]http://img233.imageshack.us/img233/788/diskt.th.jpg[/IMG]](http://img233.imageshack.us/i/diskt.jpg/)

This is my current menu.lst

[http://pastebin.com/m140be1e5](http://pastebin.com/m140be1e5)

Any ideas why it can not see partitions when booting with the larger harddisk ?

I think it might have been the clone software that I used does any one recommend some thing that will also clone the MBR area ?

---

### Post by mikewhatever on 2009-09-23
Check the uuid of the new root partition with **sudo blkid**, it's probably a different one to that you have in the menu.lst (see below).
#
kernel          /boot/vmlinuz-2.6.20-15-generic root=**UUID=0b77b069-d566-4e2e-989a-b68dab3636ee** ro quiet splash

---

### Post by SimonT on 2009-09-23
Thanks for the hint I will install the new drive boot up a live cd and see if I can get the UUID, As I dont think you can get this from windows.

---

### Post by SimonT on 2009-09-23
Current drive

ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="BC78488E784848FA" TYPE="ntfs"
/dev/sda2: TYPE="swap" UUID="faa0dea0-9647-4872-b189-df01a91ddbcc"
/dev/sda3: UUID="0b77b069-d566-4e2e-989a-b68dab3636ee" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda4: UUID="064d9848-ad9a-48fa-bd9c-ebe71d14b1d3" SEC_TYPE="ext2" TYPE="ext3"

with new drive attached by USB

ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="BC78488E784848FA" TYPE="ntfs"
/dev/sda2: TYPE="swap" UUID="faa0dea0-9647-4872-b189-df01a91ddbcc"
/dev/sda3: UUID="0b77b069-d566-4e2e-989a-b68dab3636ee" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda4: UUID="064d9848-ad9a-48fa-bd9c-ebe71d14b1d3" SEC_TYPE="ext2" TYPE="ext3"
/dev/sdb1: UUID="faa0dea0-9647-4872-b189-df01a91ddbcc" TYPE="swap"
/dev/sdb2: UUID="0b77b069-d566-4e2e-989a-b68dab3636ee" TYPE="ext3"
/dev/sdb3: UUID="064d9848-ad9a-48fa-bd9c-ebe71d14b1d3" TYPE="ext3"
/dev/sdb4: UUID="BC78488E784848FA" TYPE="ntfs" 

So what drive should I change in my menu.lst and replace as the new UUID ?

---

### Post by rreese6 on 2009-09-23
I believe it is possible to replace the UUID with the device
such as /dev/sda3 . once grub is up just hit e to edit and replace the UUID with the device.
try to substitute this for the entire UUID=xxxxxxxxxxxxxxxxxxxxxxxxxx part. "root=/dev/sda3" (without quotes).

in /boot/grub/menu.lst

kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=0b77b069-d566-4e2e-989a-b68dab3636ee ro quiet splash

kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=0b77b069-d566-4e2e-989a-b68dab3636ee ro single

change to:

kernel          /boot/vmlinuz-2.6.20-15-generic root=/dev/sda3 ro quiet splash

kernel          /boot/vmlinuz-2.6.20-15-generic root=/dev/sda3 ro single

Let me know how this works out for you. the drive is known by taking the hd nuber and coverting. (hd0,2) is first drive(sda),partition(3).
counting starts at 0 not 1, so 0=1 1=2 2=3 etc.

once it is up do the blkid again to get the real numbers and reverse operation.
I have done this on various hd's sucessfully.

---

### Post by SimonT on 2009-09-23
One thing I could do is as the system is cloned on to the new drive is look what partition currenty has the

UUID=0b77b069-d566-4e2e-989a-b68dab3636ee 

and then see what it is on the clone drive


/dev/sdb1: UUID="faa0dea0-9647-4872-b189-df01a91ddbcc" TYPE="swap"
/dev/sdb2: UUID="0b77b069-d566-4e2e-989a-b68dab3636ee" TYPE="ext3"
/dev/sdb3: UUID="064d9848-ad9a-48fa-bd9c-ebe71d14b1d3" TYPE="ext3"

---

### Post by rreese6 on 2009-09-23
if you notice that the UUID is the same. this is what is causing your problem. try my method  by editing the grub selection....
in grub hit "e" then select the kernal line and hit "e" again.
back arrow until the end of the UUID number...backspace to the "=" after the word root, type in "/dev/sda3" (no quotes)
so it will now read "root=/dev/sda3" hit enter
then type "b" to boot. if it works, then modify /boot/grub/menu.lst
as in my last post.

---

### Post by SimonT on 2009-09-23
Sorry i did not even notice the UUID is the same will try it as soon as I finnish work.

---

### Post by rreese6 on 2009-09-23
No worries! Don't be sorry, we are having Fun here...I am just used to Linux for years, so I read everything....the info is not a bunch of alien speak like another OS I used to use...It actually is usable most of the time...Besides I am taking the evening just to hang out and help folks here....:popcorn:

---

### Post by mikewhatever on 2009-09-24
The uuid of sda2 is obviously the same, so that's not the problem. However, if Ubuntu is now on sda2, Grub is looking on sda3 because of (hd0,2). Grub starts counting from zero, so that (hd0,0) is the first partition, (hd0.1) the second, and (hd0,2) the third. I am not sure why you have that line in the menu. I have another uuid instead. However it may be, (hd0.2) points grub to sda3, and the uuid line to sda2.

```
title           Ubuntu 9.04, kernel 2.6.28-15-generic
uuid            446a4fa4-51be-4071-bf8e-20b1f96ce13f
kernel          /boot/vmlinuz-2.6.28-15-generic root=UUID=446a4fa4-51be-4071-bf8e-20b1f96ce13f ro quiet splash quiet 
initrd          /boot/initrd.img-2.6.28-15-generic

```

---

### Post by SimonT on 2009-09-24
I will remove the current drive and take the cloned disk out of the USB caddy and install it and rerun the tests and check uuidd as well as testing whats said here.

---

### Post by rreese6 on 2009-09-24
ok let us know how it works out

---

### Post by SimonT on 2009-09-24
Ok removed the old disk and tock the new larger disk out of the usb caddy and installed it.

On boot I received the error 15 **at this time it did not allow me to edit my grub menu.**

I rebooted with a live cd once logged in I ran blkid

> ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: TYPE="swap" UUID="faa0dea0-9647-4872-b189-df01a91ddbcc" 
/dev/sda2: UUID="0b77b069-d566-4e2e-989a-b68dab3636ee" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="064d9848-ad9a-48fa-bd9c-ebe71d14b1d3" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="BC78488E784848FA" TYPE="ntfs" 


Will now look to see if I can do a manual edit of my grub menu with the ideas given and reboot and see if I get the menu.

---

### Post by SimonT on 2009-09-24
Crap in the live cd when I tried to use the text editor and save the file I get permission denied 


I tried sudo gedit menu.lst but still would not allow me to save it.

Any ideas ?


Will put the old disk back in and keep looking.

---

### Post by rreese6 on 2009-09-24
ok that is probably because the disk is mounted as read-only.
what you need to do is unmount it and remount it. 


 do this with hd in comp and boot off of cd rom
```

umount /dev/sda3 
cd /media
mkdir sda3
mount /dev/sda3 /media/sda3
```
This will mount the hard drive so it can be written to.
then do this

```
cd sda3/boot/grub
sudo gedit menu.lst

```
Save it
then reboot
and all done

---

### Post by SimonT on 2009-09-28
Ok based on the commands above I used this commands

```
ubuntu@ubuntu:~$ umount /dev/sda2
ubuntu@ubuntu:~$ cd /media
ubuntu@ubuntu:/media$ ls
disk-1
ubuntu@ubuntu:/media$ sudo mkdir sda2
ubuntu@ubuntu:/media$ sudo mount /dev/sda2 /media/sda2
ubuntu@ubuntu:/media$ cd sda2/boot/grub
ubuntu@ubuntu:/media/sda2/boot/grub$ sudo gedit menu.lst

```

Now at last able to save menu.lst this is what it looks like

```

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=0b77b069-d566-4e2e-989a-b68dab3636ee ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=0b77b069-d566-4e2e-989a-b68dab3636ee ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
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
root		(hd0,2)
savedefault
makeactive
chainloader	+1

```

Saving and rebooting wish me luck

---

### Post by SimonT on 2009-09-28
No luck still getting error 15 when booting did I miss understand about setting the correct "root" value ?

---

### Post by presence1960 on 2009-09-28
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by SimonT on 2009-09-28
Thanks presence1960, I found the link in your sig a little while before you posted and read through the code and thought this would be handy to use/fault find. I am at work right now but will try and do it when I go home for lunch.

---

### Post by presence1960 on 2009-09-28
> **SimonT said:**
> Thanks presence1960, I found the link in your sig a little while before you posted and read through the code and thought this would be handy to use/fault find. I am at work right now but will try and do it when I go home for lunch.

No problem. I will check back in the morning. it is 11:00 pm here and I will be going to bed in a little while.

---

### Post by SimonT on 2009-09-28
Handy little script :-)

```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 7.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2ad51cdd

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       979,964       979,902  82 Linux swap / Solaris
/dev/sda2             979,965    14,651,279    13,671,315  83 Linux
/dev/sda3          14,651,280    30,941,189    16,289,910  83 Linux
/dev/sda4    *     30,941,253   117,210,239    86,268,987   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: TYPE="swap" UUID="faa0dea0-9647-4872-b189-df01a91ddbcc" 
/dev/sda2: UUID="0b77b069-d566-4e2e-989a-b68dab3636ee" TYPE="ext3" 
/dev/sda3: UUID="064d9848-ad9a-48fa-bd9c-ebe71d14b1d3" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="BC78488E784848FA" TYPE="ntfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda2 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)


=========================== sda2/boot/grub/menu.lst: ===========================

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
default		4

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=UUID=0b77b069-d566-4e2e-989a-b68dab3636ee ro

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

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=0b77b069-d566-4e2e-989a-b68dab3636ee ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=0b77b069-d566-4e2e-989a-b68dab3636ee ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
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
root		(hd0,2)
savedefault
makeactive
chainloader	+1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=0b77b069-d566-4e2e-989a-b68dab3636ee /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda4
UUID=064d9848-ad9a-48fa-bd9c-ebe71d14b1d3 /home           ext3    defaults        0       2
# /dev/sda1
UUID=BC78488E784848FA /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=faa0dea0-9647-4872-b189-df01a91ddbcc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

=================== sda2: Location of files loaded by Grub: ===================


   1.1GB: boot/grub/menu.lst
   1.0GB: boot/grub/stage2
   1.1GB: boot/initrd.img-2.6.20-15-generic
    .5GB: boot/initrd.img-2.6.20-15-generic.bak
   1.1GB: boot/vmlinuz-2.6.20-15-generic
   1.1GB: initrd.img
   1.1GB: vmlinuz

================================ sda4/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```

---

### Post by oldfred on 2009-09-29
Some suggestions:

Grub is looking at sda3 but Ubuntu is in sda2 - you need to reinstall grub to correct where it is pointing.

I would change your menu.lst entries for the 3 Ubuntu lines from
root  (hd0,0)
to 
UUID 0b77b069-d566-4e2e-989a-b68dab3636ee

You could use (hd0,2) but UUID are more current & less likely to change.

You also need to change the windows from (hd0,2) to (hd0,3)  since it is in sda4.

---

### Post by SimonT on 2009-09-29
Thank you for the hint oldfred 

Will make the change to menu.lst

In my menu I have two root statements I will change the first one but I thought that maybe the second one was a extra hint :-) at the location of the boot files.


One thing that is also strange I was expecting to get a new UUID as I cloned my original disk (I guess a UUID is not the same as a diskid)

> 
title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
[COLOR="Red"]root[/COLOR]		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic [COLOR="Red"]root[/COLOR]=UUID=0b77b069-d566-4e2e-989a-b68dab3636ee ro single
initrd		/boot/initrd.img-2.6.20-15-generic


To reinstall grub is it as simple as 

grub-install /dev/sda2
reboot ?

---

### Post by oldfred on 2009-09-29
There are several ways to reinstall Grub. You want to install it to the MBR of your first drive.

Supergrub is the easiest. 

If you have chroot the mounted partition (chroot ubuntu) then you can 
 grub-install /dev/hda 

sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd0,1)
root (hd0,1) #use the numbers from the previous command
setup (hd0)
# Or
6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".
quit

I believe that the reason you have the same UUID is because you cloned the drive. That is so that all the entries are the same. Normally you will not have 2 UUIDs the same.
Hopefully I pointed you the correct way. Presence usually sees something more in the way of things to fix and is clearer on way to fix them.

---

### Post by presence1960 on 2009-09-29
This is what I would do. I would first reset GRUB because GRUB is pointing to partition #3 which has no OS on it. To reset GRUB do this:

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

I would also change these in red
```

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		[COLOR="Red"](hd0,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=0b77b069-d566-4e2e-989a-b68dab3636ee ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		[COLOR="Red"](hd0,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=0b77b069-d566-4e2e-989a-b68dab3636ee ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		[COLOR="Red"](hd0,0)[/COLOR]
kernel		/boot/memtest86+.bin
```

to

(hd0,1)

As it turns out this appears to be a very simple problem. That is why I always insist on using the boot info script. If we had run that from the beginning of this thread it wouldn't have carried on for 3 pages.

P.S> according to the output from boot info script all UUID's are unique.

---

### Post by presence1960 on 2009-09-29
If you want GRUB to take over at boot It must be in MBR.

Your windows is on sda4 so your windows entry should be

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Microsoft Windows XP Professional
rootnoverify	(hd0,3)
chainloader	+1

```

---

### Post by SimonT on 2009-09-29
Thanks presence for your help and every ones else's hints and ideas.

After following the detail's I was able to reboot and have the grub menu come up. Windows would not boot as it could not find hal.dll. So back in to the live cd and changed the windows boot.ini to point to the correct partition and rebooted and I had windows and Ubuntu running again.

That script was the real key to understand what had happened when I cloned the system :-)

---

### Post by presence1960 on 2009-09-29
Glad you got it working! Enjoy Ubuntu.

---

