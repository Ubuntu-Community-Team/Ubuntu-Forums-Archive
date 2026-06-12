---
title: "Unclean shutdown error 17"
date: 2009-06-07
forum: Hardware
---

### Post by dkook on 2009-06-07
I have an HP Pavillion laptop with a seta drive. I have been trying to create a duel boot system with ubuntu 9 and vista.  Recently I put my laptop in to hibernate mode and when I went to turn it back on grub loader 1.5 gave me an error 17.  I used my ubuntu 8 cd (because I couldn't find my ubuntu 9 at the time) to boot up my computer.  I tried to force the computer to mount the drive, but ubuntu told me that the drive is in an active mode and an unclean shutdown took place.  Is there anything that I can do?

---

### Post by quixote on 2009-06-08
Do you get a command line when you try to boot?  I.e. does it dump you to the recovery console? (black screen, white letters, usually)

If so, does it tell you to run "fsck" ?  Or does it just complain about uncleanliness?

If the latter, at the prompt (which should be something like #) you could try
```
#shutdown now
```
Then start back up again and see what happens.

If it boots only to a recovery console and tells you to run fsck, then carefully read the screen to see which drive (aka "partition") needs to be checked.  It'll look something like /dev/sda1 or /dev/hda2.  Then run
```
fsck -y /dev/sdx#
```
(Substitute whatever the message says is the correct device designation.)  The -y tells it to answer all questions with a "yes" which, at least for me since I have no idea what it's doing, is the only option anyway.

Important: do NOT run fsck unless you're in a recovery console or you are sure the drive / partition being checked is not mounted (ie not active).

Hope this helps!

---

### Post by dkook on 2009-06-11
Sorry for not getting back getting to a computer has been difficult .  Unfortunately the suggestion about a command prompt won't work because nothing happens after the error 17 pops up.  However I have gotten access to my documents on the drive using Ubuntu 8.04.  However the other suggestions that I have seen about using gparted to unmount or hooking it up to a windows machine to safely remove the hard ware don't work.  I believe the problem stems from the computer being put into hibernate mode without battery power which caused a shutdown of the system.  Ubuntu mounts and unmounts the drive fine, but doen't resolve the problem.  Windows says the drive is still active and can't safely remove it.
 
Is there a way to create a boot disk into windows? 
 
I am going to try to hook it to windows again and have it scan the drive for error to see if I can resolve this problem.
 
Thanks for the help.

---

### Post by quixote on 2009-06-12
I'm having a bit of trouble figuring out what the status is right now.

You can boot into Windows, but it says the drive you want to unmount is active? ?? Or you can't boot into Windows?  I assume the latter, because you're asking about a Windows boot disk.  But then, how can Windows be telling you the drive is busy?

Could you post the command you run and the actual error message that says the drive can't be unmounted? 

Also, if you have it booted up via ubuntu LiveCD, could you post the output of ```
sudo fdisk -l
``` (that's "l" as in "list")

There are certainly such things as windows boot disks.  Possibly one came with your computer?  In the Good Old Days, bootable Windows drives had a program on them called "fixmbr".  Boot from that drive and at the DOS prompt just type that command.  It fixes the Master Boot Record so Windows can see it again.

Getting Ubuntu working again after that would just mean reinstalling grub. Two useful sites: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)   [http://www.supergrubdisk.org/w/index.php5?title=Boot_Problems](http://www.supergrubdisk.org/w/index.php5?title=Boot_Problems)

It's hard not to get really frustrated with this stuff, but remember that everything is still there.  Right now it's just that the operating systems don't know where the doorbells are to get into the right apartments.  That's solvable!

---

### Post by dkook on 2009-06-12
Thanks for sticking with me.  
 
I have been using ubuntu 8.04 livecd to access files and try other suggestions that I have seen and I will try to get use the fdisk command as soon as I can and post the results. 
 
I have also used my wife's vista laptop to access the drive with a usb adapter because I saw a suggestion elsewhere to do that and to use the safely remove hardware to fix the problem.  All I get is a message from windows that the drive is active and to close the program that is accessing the drive or something to that effect.  However, I think that is has to do with the adapter not necessarily the drive or its problems.  
 
 
Hope this helps clarify the issues

---

### Post by dkook on 2009-06-13
Tried the fdisk and got:
[SIZE=1]Disk /dev/sda: 250.0 GB, 250059350016 bytes[/SIZE]
[SIZE=1][/SIZE]
[SIZE=1]255 heads, 63 sectors/track, 30401 cylinders[/SIZE]
[SIZE=1][/SIZE]
[SIZE=1]Units = cylinders of 16065 * 512 = 8225280 bytes[/SIZE]
[SIZE=1][/SIZE]
[SIZE=1]Disk identifier: 0x801aa204[/SIZE]
[SIZE=1][/SIZE]
[SIZE=1] [/SIZE]
[SIZE=1] [/SIZE]
[SIZE=1]   Device Boot      Start         End      Blocks   Id  System[/SIZE]
[SIZE=1][/SIZE]
[SIZE=1]/dev/sda1   *           1       15684   125976420    7  HPFS/NTFS[/SIZE]
[SIZE=1][/SIZE]
[SIZE=1]/dev/sda2           15685       28814   105466725    5  Extended[/SIZE]
[SIZE=1][/SIZE]
[SIZE=1]/dev/sda3           28815       30401    12747577+   7  HPFS/NTFS[/SIZE]
[SIZE=1][/SIZE]
[SIZE=1]/dev/sda5           15685       16045     2899669+  83  Linux[/SIZE]
[SIZE=1][/SIZE]
[SIZE=1]/dev/sda6           16046       16069      192748+  82  Linux swap / Solaris[/SIZE]
[SIZE=1][/SIZE]
[SIZE=1]/dev/sda7           16070       28275    98044663+  83  Linux[/SIZE]
[SIZE=1][/SIZE]
[SIZE=1]/dev/sda8           28276       28814     4329486   82  Linux swap / Solaris[/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1]Some of the partitions are from attempts to install ubuntu proir to this problem. [/SIZE]
[SIZE=1][/SIZE]
[SIZE=1][/SIZE]

---

### Post by dkook on 2009-06-13
I went to the recovering ubuntu ([[COLOR=#444444]https://help.ubuntu.com/community/Re...tallingWindows[/COLOR]]("https://help.ubuntu.com/community/Re...tallingWindows")) webpage and went throught the steps it suggests to overwrite the windows bootloader. I got to grub> and using the find command I got (hd0,4), but that is as far as it went. When I tried the root(hd0,4), I get error 27: nrecognized command. I went on to do the setup command and got error 12:invalid device requested.
 
Continuing onward with the page, I used the command gksu gedit /boot/grub/menu.lst, but when the editor opened, it was blank.  Not sure where to proceed from here.

---

### Post by dkook on 2009-06-13
Thank you!  One down one to go.
 
Super grub disk got me to the point were it would load windows again, but when I restarted the same error comes up.  The SGD has a lost of options but none of them will load the Ubuntu that is on the on one of the partitions.  It gives me an error 15.  Does that mean that the grob loader on the hard drive is bad and should be fixed?  If so, how?  The SGD gave me dire warnings when I entered into that part of the program, so I stopped before I did anything else.

---

### Post by dkook on 2009-06-13
Well the trouble increased a bit when I tried to create restore disks.  The system couldn't access the restore side of the hard drive.  I don't know if this has anything to do with the error 17.

---

### Post by quixote on 2009-06-13
Which Ubuntu are you running?  Intrepid (8.10)?  Jaunty (9.04)?  The latter can have a new kind of grub that doesn't use menu.lst, but I thought you had to install the new grub on your own, and I doubt you've done that.  So the fact that you don't have anything in /boot/grub/menu.lst is enough to explain the problems right there.

If I understand where things are at now, Windows now boots by itself, but not if grub gets in the way.  So your Master Boot Record is okay.  

Grub, I think is confused by your partitions.  Your Windows is on (hd0,0), not (hd0,4). The latter is one of your linux partitions, so it makes sense it won't boot Windows :) .  You need to be sure which of your partitions holds the active ubuntu install.  Grub said sda5 (that's what hd0,4 means), but since that didn't work, try (hd0,6) and hope for the best.  (hd0,6 = sda7) 

Here's a sample menu.lst file.  I doubt it'll work as is, but at least it'll give you something to start with.  Lines beginning in # are comments. The actual uncommented code is in red.  You could copy and paste this into your menu.lst (assuming font colors DON'T carry over).
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
[COLOR="Red"]default		1[/COLOR]
## ## ##IMPORTANT: This determines the default OS to boot into.  Grub counts from zero, so I've set it at your second option: Windows.  If you wanted to set this to Ubuntu, it would be  0. If the recovery option was uncommented, it would be second, Windows would be 3rd, and default would become 2.

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
[COLOR="Red"]timeout		10[/COLOR]
## ## You can set this to 30 seconds, or 1.  Or anything.  whatever works for you.

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
# kopt=root=UUID=78b9d228-030a-431b-b1ce-49a7b3e32101 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=78b9d228-030a-431b-b1ce-49a7b3e32101

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

### END DEBIAN AUTOMAGIC KERNELS LIST


[COLOR="Red"]title		Ubuntu 8.10
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.27-14-generic
root		(hd0,6)
initrd		/boot/initrd.img-2.6.27-14-generic
savedefault
boot[/COLOR]

##usually there's a recovery mode option that goes here, but I don't know what the partition designations would be for your system
#title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
#root		(hd0,6)
#kernel		/boot/vmlinuz-2.6.27-14-generic 
#root		(hd0,6)
#initrd		/boot/initrd.img-2.6.27-14-generic
#savedefault
#boot

[COLOR="Red"]title		Windows Vista
root		(hd0,0)
savedefault
makeactive
chainloader	+1[/COLOR]

```

Important: make sure the kernel and initrd lines point to the location of the files on your system.  Sometimes they're in the topmost (/) directory.  Sometimes, as above, they're in /boot.  Alter those lines so they match the path and filenames on your system.

---

### Post by dkook on 2009-06-14
I am running both Ununtus. I am using 8.10 livecd, but 9.04 is installed on the harddrive. I lost track of my 9.04 cd.
 
I'll try your solution when I gt a chance.  Thanks again.

---

