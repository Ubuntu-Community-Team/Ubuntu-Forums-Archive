---
title: "Upgrade from 9.04 prob: mounts in fstab can't be mounted"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by Shaqdeeez on 2009-10-31
Dell Dimension E310, one hard drive, only runs ubuntu.

So i started the upgrade from 9.04 to 9.10 last night through update manager. The download was going to take several hours so i just let it run last night.  This morning the screen was blank and non-responsive.  After a hard restart i see the typical kernel option from 9.04 and the usual splash screen with some scrolling text and then:

"one or more mounts listed in /etc/fstab cannot yet be mounted: (ESC for recovery shell)
$/: waiting for /dev/disk/by-uuid/abeedd62-48a0-4c38-91d6-85d64fe42bee
$:/tmp: waiting for (null)
swap: waiting for UUID: f15f3ec6-5047-403e-9f4e-3d8adaa79027 "
-----------
the contents of fstab currently look like:

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=a6eedd62-48a0-4c38-91d9-85d64fe42bee /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f15f3ec6-5047-403e-9f4e-3d8adaa79027 none            swap    sw              0       0
/dev/scd1       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0
-------------------------------
The contents of menu.lst look like:

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        2

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=a6eedd62-48a0-4c38-91d9-85d64fe42bee ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a6eedd62-48a0-4c38-91d9-85d64fe42bee

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
# defoptions=splash vga=773

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

title        Ubuntu 9.04, kernel 2.6.28-16-generic
uuid        a6eedd62-48a0-4c38-91d9-85d64fe42bee
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=a6eedd62-48a0-4c38-91d9-85d64fe42bee ro splash vga=773 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid        a6eedd62-48a0-4c38-91d9-85d64fe42bee
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=a6eedd62-48a0-4c38-91d9-85d64fe42bee ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        a6eedd62-48a0-4c38-91d9-85d64fe42bee
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=a6eedd62-48a0-4c38-91d9-85d64fe42bee ro splash vga=773 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        a6eedd62-48a0-4c38-91d9-85d64fe42bee
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=a6eedd62-48a0-4c38-91d9-85d64fe42bee ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        a6eedd62-48a0-4c38-91d9-85d64fe42bee
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=a6eedd62-48a0-4c38-91d9-85d64fe42bee ro splash vga=773 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        a6eedd62-48a0-4c38-91d9-85d64fe42bee
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=a6eedd62-48a0-4c38-91d9-85d64fe42bee ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        a6eedd62-48a0-4c38-91d9-85d64fe42bee
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
---------------------------------------------------------

Any ideas on how to fix?

---

### Post by Gitykins on 2009-10-31
I have the same problem (different UUID of course), and I've found that neither /dev/disk or any /dev/sdaX or sdbX exists on the Karmic partition.

I upgraded in terminal from 9.04

---

### Post by wcorey on 2009-10-31
I have the same problem upgrading my 3rd machine. First two 32bit laptop, and 64bit LVM went flawlessly.

How do I get to / even off a LiveCD? 

Based on what you see are you implying those directories are gone entirely? I would really like to, at least, save /home if not be able to complete or redo install from livecd while preserving that data.

I found another post where they changed the menu.lst to point to 2.6.31.14 and that worked for 2 people. Is it safe to take one of the menu.lst files from a properly configured 9.10 and simply replace it on the errant machine, once I save the existing 'bad' one? But first I have to be able to mount the / drive from a live cd. H thought the live cd mounted itself as /.

---

### Post by carvao on 2009-10-31
i'm having the same problem

---

### Post by MidGe48 on 2009-10-31
Leading up to my current problem:
 

 
[LIST=1]
[*]Upgrading from Jaunty to Karmic
[*]Upgrade hangs up.. with no disk 	activity
[*]On reboot no more xorg-xserver
[*]Message “One of more mounts 	listed in etc/fstab cannot yet be mounted”
 	/: waiting for 	/dev/disk/by-uuid/376...
 	/tmp: waiting for (null)
 	swap: waiting for UUID=6a3...
[*]I can escape to a shell, can login 	as root or as user
[/LIST]
 

 Problem:
 

 
[LIST=1]
[*]I cannot continue the upgrade
[*]A file-system is registering as 	read-only
[*]fsck on the file system shows no 	error
[*]xorg is not installed properly
[*]From another Karmic partition 	(full install successful), I can access read-only the partition that 	seems to give the problem. So the data is all there.
[*]Neither apt, dpkg, even editors work because of the read-only on the file system
[/LIST]
 

 Solution:  
 
[LIST=1]
[*]I am most definitely looking for 	one and can give more information as needed
[*]I could not find an answer after 	having googled close to a hundred entries .
[*]Has anyone got any ideas about how 	to go about this? I am a relative newbie, and am quite stumped here.
[/LIST]
 

 Thanks for any help
 

 

 Michel
 
[LIST=1]
[LIST=1]
[LIST=1]
[*]
[/LIST]
[/LIST]
[/LIST]

---

### Post by georgewsu on 2009-10-31
Take a look at this thread:
[http://old.nabble.com/URGENT:-Problem-with-mounting-td26125463.html](http://old.nabble.com/URGENT:-Problem-with-mounting-td26125463.html)

I had some of the same problems, and I was able to solve it by:
-booting from live cd
-mounting my partition
-chroot to my partition
-sudo update-grub
-sudo dpkg --configure -a

I didn't have the read-only problem, but that thread has a solution for it.

Hope that helps.

---

### Post by iwansetiawan on 2009-11-01
I solve it by edit /etc/fstab:
- Disable fsck on vfat, like mentioned in [here]("http://techflock.blogspot.com/2007/05/slow-ubuntu-bootup-disable-fsck-on-vfat.html")
- and change UUID by /dev/sdxx

---

### Post by Shaqdeeez on 2009-11-01
[SOLVED]
This took a while and was rather involved.
edits to menu.lst were unsuccessful.
edits to fstab were unsuccessful.

a version of [georgewsu]("http://ubuntuforums.org/member.php?u=942456") 's suggestion worked.
-booting from ubuntu 9.04 live cd
-mounting my partition at /media/disk by selecting it in places pulldown menu on desktop
-chroot to my partition by typing " sudo chroot /media/disk " in terminal window
- got this error: /dev/null: Permission denied, fixed this by typing: " rm /dev/null " in terminal window and it went away as suggested by [tuxcantfly]("http://ubuntuforums.org/member.php?u=79823") .
- " sudo update-grub " was successful
- " sudo dpkg --configure -a " eventually failed due to too may errors.
- At this point I took out my usb wifi and connected an ethernet cable. not sure if that made a difference or if updating grub was the key to the fix.
- closed terminal despite error message that process was still running.
- restarted and ejected live cd.
- startup took a while as the disk was checked.
- new kernel loaded but went to command line only. logged in.
- " sudo dpkg --configure -a " was successful.
- " sudo shutdown -r now " to reboot
- finally made it to karminc!

---

### Post by tsh on 2009-11-03
I have the same problem - Although there is a prompt to press escape for a rescue shell, this does nothing. Since the instructions above may seem a bit cryptic, here is what I am doing:

1) Boot from a live CD. I'm using 6.06, since I have one to hand. 

2) Application/accesories/terminal for a shell.

3) 'mount' to see if any drives are mounted and see where we are. Only my external hdd is mounted, not my system disks.

4) System/Admin/Disks: shows 3 disks. None are accessible. Need to mount the root partition with an access path of /media/root. In order to do this, 6.06 needs a new directory (change, new) and 'enable'

5) in the shell 'cat /media/root/etc/fstab' to check how the partitions are set up in case you forgot since you did your original install. Editing to revert the UUID might be an option here if all else fails.

6) in order to chroot, the root partition needs to be mounted without 'noexec, nosuid'.
mount to get the drive and fstype
un-mount the drive
sudo mkdir /media/root
sudo mount /dev/sda1 / -t ext3 (As apropriate)
sudo chroot /media/root

7) sudo update-grub

8) sudo dpkg --configure -a

Hmmm... I now have a system which boots to a prompt, no X.

---

### Post by klugja on 2009-11-04
I also had a failed upgrade, and couldn't automatically mount root.

My /sbin/vol_id was missing.

Here is what I did:


sudo cp /sbin/vol_id /media/disk/sbin
sudo mount -t proc none /media/disk/proc
sudo mount -o bind /dev /media/disk/dev
sudo chroot /media/disk
sudo update-grub
sudo dpkg-configure -a

I had a few errors in dpkg-configure, but it finished.

Then I could reboot to X, and my NIC worked.  The update manager refused to work, saying something about not being able to go from karmic to jaunty.

I then went into aptitude, did a capital U, and g.  Most stuff was already downloaded, and it just went.  So now the update manager says everything is up to date. 

About says I have karmic koala, so I think I'm there!  I even installed google chromic just to prove the package manager works.

---

### Post by nightshade209 on 2009-11-07
I have the same problem, and i tried the solution given above. However, at the ```
sudo update-grub
```, i get the following error: ```
sudo update-grub
sudo: unable to resolve host ubuntu
sh: cannot create /dev/null: Permission denied
sh: cannot create /dev/null: Permission denied
Searching for GRUB installation directory ... found: /boot/grub
findfs: unable to resolve 'UUID=e59eb16e-0384-4f12-9514-99a8c9eadb44'
Cannot determine root device.  Assuming /dev/hda1
This error is probably caused by an invalid /etc/fstab
/usr/sbin/update-grub: line 390: /dev/null: Permission denied
/usr/sbin/update-grub: line 251: /dev/null: Permission denied
/usr/sbin/update-grub: line 257: /dev/null: Permission denied
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found kernel: /boot/vmlinuz-2.6.28-16-generic
Found kernel: /boot/vmlinuz-2.6.28-15-generic
Found kernel: /boot/vmlinuz-2.6.28-14-generic
Found kernel: /boot/vmlinuz-2.6.28-13-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
sed: warning: failed to get security context of /tmp/fileNoLsUr: No data availableCan't open /dev/null: Permission denied

```
Also, dkpg --configure -a returns too many errors. Pls help.

---

### Post by tamerlaha on 2009-11-08
i have a some problem at acer aoa-110 but  not alltimes and after pressing esc its booting up ... im confused (
up: i changed /etc/fstab/  set mount not by uuid, but by /dev/sda1
and a 3 times its boot fine, hope it was helpfull for my.


up2: nope its does not help ((

---

### Post by unix1adm on 2009-11-13
i am having this issue too.. When I try to update things i get the following error..


Setting up virtualbix-ose-source (3.0.8-dfsg-1ubuntu)...
Adding modules to DKMS build system
Doing inital module builds

Error! Your kernel source for kernel 2.6.27-7-generic cannot be found at /lib/modules/2.6.27-7-generic/build or /lib/modules/2.6.27-7-generic/source.
dkpg: error processing virtualbox-ose-source (--configure):
subprocess installed post-installation script returned error exit status 1
Error were encountered while processing:
virtualbos-ose-source

---

### Post by unix1adm on 2009-11-13
all i can say is that this is the WORST upgrade of an OS i hav ever done. I work on AIX and other Linux and nothing like this has ever happend to me in the past. So many people with same or similar problems. I gotta wonder did they test teh code before telling people it was readny to be upgraded. 

very very dissapointed in this process.

---

### Post by simmcrd on 2009-11-15
I've been using Karmic for 2 months now (prerelease). I had no problem until apt replaced kernel 2.6.31-10-generic with 2.6.31-11-generic. Since 2.6.31-11-generic, and with every new kernel kernel (including the current 2.6.31-14-generic) I've had the very problem you describe.

My work around: set grub to default to 2.6.31-10-generic. If you don't have it, 

- Download the .deb with a another computer. 
- Upload via USB thumbdrive or net. 
- dpkg -i the .deb. 
- Ensure 2.6.31-10 is the default boot image.

I hope this helps.

---

### Post by steven_pack on 2009-11-15
Just upgraded from 9.04 to 9.10... same error as everyone here.

It was on a Dell Vostro 1000, bog standard business laptop from Dell.

That's the end of the Linux experiment I'm afraid.

---

### Post by simmcrd on 2009-11-16
**NEW FIX!!!**

The problems seems to be with the "mountall" command.

[LIST=1]
[*]Hit ESC then enter your root password
[*]type "**mount -v -w -n -o remount /**" to remount your root filesystem read-write
[*]now type "**mount -v -a**", _do NOT use mountall_, use mount
[*]type "**swapon -v -a**"
[*]that should to it. Type "**exit**" to get out of special seesion and to resume boot. Voila!
[/LIST]

---

### Post by unix1adm on 2009-11-19
Well I may have some good news.. no solution but I did find a month old back up of my system i had on a drive at work so I am going to buy another 250G drive(compusa 69$). Rebuild to 9.4. if that works then I will at least have my old system back and I can continue to work on this issue as time allows without being so panicked to get my machine back.

Talked to several people i know that know Ubuntu and they all agree Ubuntu dropped the ball with the migration process.

They recommended the clean install method. But the migration has many issues.
However it is possible to recover from this so I may just keep plugging at it once I get my 9.4 image back. I wont try a migration again for some time and when I do Ill be sure to keep a current copy on the other disk.

Maybe Ill create a new partition and run 2 version of Ubuntu before upgrading that way I can mount the old one to the new one and copy my user data over as needed. Then once verified it works I can backup and remove the old image after a few days/weeks of testing.

This is what I do for my AIX systems at work so time to implement this at home...

---

### Post by danlea on 2009-12-01
Adding my experience with this issue.  I too tried to upgrade the GUI way and my screens went blank mid-way, followed after a short time by zero disk activity (possibly a prompt).  This has happened to me before - I just forgot about it.  Next time I'm upgrading in recovery mode.  Anyway...

Couldn't boot into normal or recovery mode as I had the fstab error and couldn't escape to a prompt.  I'm not sure if it was me pre-empting the error message with presses of the escape button, or copying the contents of /dev/disk to my real Ubuntu partition from the filesystem of a Live CD boot (my real /dev folder was pretty bare), but I finally did manage to escape to a prompt.

From here I used ```
mount -n -o remount,rw /
``` to make my drives writeable.  I don't believe I needed to use ```
mount -v -a
``` but I did have to enable the swap with ```
swapon -v -a
```  update-grub was then successful, but I'm not sure it actually did anything for me.

The next step was to run ```
apt-get -f install
``` and then ```
apt-get upgrade
```  This got me to a usable system, and from there I could finish the upgrade from GDM.

It took me a whole working day to do this, but hopefully this will help anyone else experiencing the problem, and thanks to everyone who's posted good advice here and in other topics/forums - it certainly would have taken me a lot longer to solve without it.

---

### Post by wavesailor on 2009-12-15
This worked for me and my system just hung after boot up with the same message. I hit "ESC" and followed the instrunctions below and then rebooted:
[http://newyork.ubuntuforums.org/showpost.php?p=8151569&postcount=10]("http://newyork.ubuntuforums.org/showpost.php?p=8151569&postcount=10")

---

### Post by hogar.strashni on 2010-03-24
don't be so sure it is solved :(

@kentaur, @danlea, @simmcrd I tried what you posted but it didn't work for me.

I'll post my problem in new thread because this one's closed - or at least marked as SOLVED. Far away from solved to me :(

Looking forward for your help :)

---

