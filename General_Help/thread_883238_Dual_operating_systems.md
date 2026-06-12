---
title: "Dual operating systems"
date: 2008-08-07
forum: General Help
---

### Post by bones16v on 2008-08-07
So I just put ubuntu on my pc, I had vista.  Before I installed it,  I was asked if I wanted to put it on a small partition or the whole hard drive, I just put it on the whole hard drive...now I want to put vista (or xp) back on so i can use it for playing games...how would I go about doing this?

---

### Post by abazoskib on 2008-08-07
do you have a vista installation CD? if so, put the CD in and reboot. it will guide you from there i think

---

### Post by lukjad on 2008-08-07
I think that there is a way to partion the Hard Drive to allow Vista to reinstall without wiping the drive. I don't know how though since I never had the need to do so.

---

### Post by steveneddy on 2008-08-07
Make another partition, install Vista from the CD/DVD, go back when finished and install GRUB bootloader to the MBR.

---

### Post by damoxc on 2008-08-07
You'll probably want to install gparted for an easy way to do this. Or use the Ubuntu Desktop CD which has gparted included for such tasks.

---

### Post by rraj.be on 2008-08-07
You can just install xp or vista in a new partition.Its just like normal installation of xp.


Edit:
```

Use Gprated to resize or make a new partition.

You have gparted in your live cd itself.
```
But at the end, the xp boot loader will not identify ubuntu.It will rewrite the MBR with its own.

You have to just reinstall GRUB BOOTLOADER of ubuntu.To reinstall GRUB follow this.

1) Boot into live cd

2) Open terminal [Application's --> Accessories --> Terminal]

3)type```
 sudo grub

find /boot /grub/stage1
```

if it returns like ```
(hdX,Y)
```

type ```
root (hdX,Y)

setup (hdx)

quit 

sudo reboot

```

Thats it.

---

### Post by cybrsaylr on 2008-08-08
I always dual booted from XP or Vista to Ubuntu.

If you just did it recently you may want to start over again.
Wipe the drive clean, put Vista back in then use your Ubuntu live CD to do a dual boot system. I did it this way to have both OSs available even though lately spend 95% of the time on linux.

---

### Post by bones16v on 2008-09-15
ok so I did everything you guys said to do, i got windows started booted it played some games and **** for awhile ( i used windows xp and it came with vista so its pretty new) finding drivers was a bitch.  anyways then i went and did the grub stuff and booted ubuntu again, now i cant boot windows anymore????  it doesnt even show up in bios

---

### Post by bones16v on 2008-09-16
anyone?

---

### Post by niglet101 on 2008-09-16
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by rraj.be on 2008-09-16
> **bones16v said:**
> anyone?


Could you post the content of 

```
sudo fdisk -l
```

And ```
gedit /boot/grub/menu.lst
```

---

### Post by mb_webguy on 2008-09-16
When you reinstalled Ubuntu, did you select the "whole drive" option again, or did you install it to its own partition?  If you selected to install to the entire drive, then you installed Ubuntu over Vista.

Here's what you need to do to have a good dual-boot installation of Vista and Ubuntu.[LIST=1]
[*]BACK UP ALL OF YOUR FILES!!!
[*]Boot your computer from the Vista installation disc.
[*]When it asks you to select the drive or partition on which to install Vista, delete all of the existing partitions (which will remove all data on those partitions, which is why I used all caps and three exclamation points in step #1).
[*]Create a new partition on which to install Vista.  25GB should be sufficient.  If you are required to specify the partition size in MB, then it may be using 1,000,000 bytes for 1MB instead of the usual 1048576 bytes.  This means that a 25GB partition which would normally be 25600MB would need to be declared as 26844MB.
[*]Finish the Vista installation as normal.
[*]Once you have finished installing Vista, boot from the Ubuntu installation disc.  At the menu, choose to install Ubuntu.  (You may also choose to boot from the LiveCD and open the installer using the icon on the desktop.)
[*]When prompted to select the partition on which to install Ubuntu, you need to create 4 new partitions.  [LIST][*]First, create a 10GB partition, formatted as ext3, and use this as the root ("/") partition.
[*]Next create a partition equal in size to 1.25x your system memory, and use this as swap.
[*]Next, create a 1GB partition, formatted as ext3, and use this as your home ("/home") partition.
[*]Finally, create a partition using the remaining drive space, and format is as NTFS.  Mount this as something meaningful, like "/media/MyFiles".[/LIST] 
[*]Make sure that you do NOT do anything to the partition on which you installed Vista.  If the partition is set to be mounted (probably as something like "/media/Windows", change this so that the drive is not mounted under Ubuntu.
[*]Finish the Ubuntu installation.    
[/LIST]

Now, you have a dual-boot installation with Vista and Ubuntu.  However, you need to make a few minor changes.  Remember that new NTFS partition we made?  Well, you're going to use that for storing all of your files.  

Boot into Vista, right-click on Start->Computer, and select Manage.  In the sidebar, select Manage Drives.  Select the NTFS partition and mount it as whatever letter you want.  Now close that and open your User folder.  Right-click on each of your folders (like "Documents" and "Music") and open the properties.  Change the location of the folder to the new drive.

Now boot into Ubuntu.  Open the terminal, and type "ls".  You should see some folders like "Documents" and "Pictures" listed.  For each of these folders, type "rm <foldername>" to delete the folder, then "ln -s /media/MyFiles/<foldername> <foldername>" to make a link to the folder on the MyFiles partition (which should be the same as the folders you moved on Vista).  If you named your NTFS partition something other than MyFiles, change that part accordingly.

Now, regardless of whether you're in Ubuntu or Vista, all of your music is in the Music folder, and all of your Pictures are in your Pictures folder, etc.  If you save an mp3 to your Music folder in Ubuntu, that mp3 will be in your Music folder in Vista.  Also, if you need to reinstall either Vista or Ubuntu, you won't lose any of your files, since the operating systems are installed to a different partition than your data.

---

### Post by bones16v on 2008-09-21
> **mb_webguy said:**
> When you reinstalled Ubuntu, did you select the "whole drive" option again, or did you install it to its own partition?  If you selected to install to the entire drive, then you installed Ubuntu over Vista.

Here's what you need to do to have a good dual-boot installation of Vista and Ubuntu.[LIST=1]
[*]BACK UP ALL OF YOUR FILES!!!
[*]Boot your computer from the Vista installation disc.
[*]When it asks you to select the drive or partition on which to install Vista, delete all of the existing partitions (which will remove all data on those partitions, which is why I used all caps and three exclamation points in step #1).
[*]Create a new partition on which to install Vista.  25GB should be sufficient.  If you are required to specify the partition size in MB, then it may be using 1,000,000 bytes for 1MB instead of the usual 1048576 bytes.  This means that a 25GB partition which would normally be 25600MB would need to be declared as 26844MB.
[*]Finish the Vista installation as normal.
[*]Once you have finished installing Vista, boot from the Ubuntu installation disc.  At the menu, choose to install Ubuntu.  (You may also choose to boot from the LiveCD and open the installer using the icon on the desktop.)
[*]When prompted to select the partition on which to install Ubuntu, you need to create 4 new partitions.  [LIST][*]First, create a 10GB partition, formatted as ext3, and use this as the root ("/") partition.
[*]Next create a partition equal in size to 1.25x your system memory, and use this as swap.
[*]Next, create a 1GB partition, formatted as ext3, and use this as your home ("/home") partition.
[*]Finally, create a partition using the remaining drive space, and format is as NTFS.  Mount this as something meaningful, like "/media/MyFiles".[/LIST] 
[*]Make sure that you do NOT do anything to the partition on which you installed Vista.  If the partition is set to be mounted (probably as something like "/media/Windows", change this so that the drive is not mounted under Ubuntu.
[*]Finish the Ubuntu installation.    
[/LIST]

Now, you have a dual-boot installation with Vista and Ubuntu.  However, you need to make a few minor changes.  Remember that new NTFS partition we made?  Well, you're going to use that for storing all of your files.  

Boot into Vista, right-click on Start->Computer, and select Manage.  In the sidebar, select Manage Drives.  Select the NTFS partition and mount it as whatever letter you want.  Now close that and open your User folder.  Right-click on each of your folders (like "Documents" and "Music") and open the properties.  Change the location of the folder to the new drive.

Now boot into Ubuntu.  Open the terminal, and type "ls".  You should see some folders like "Documents" and "Pictures" listed.  For each of these folders, type "rm <foldername>" to delete the folder, then "ln -s /media/MyFiles/<foldername> <foldername>" to make a link to the folder on the MyFiles partition (which should be the same as the folders you moved on Vista).  If you named your NTFS partition something other than MyFiles, change that part accordingly.

Now, regardless of whether you're in Ubuntu or Vista, all of your music is in the Music folder, and all of your Pictures are in your Pictures folder, etc.  If you save an mp3 to your Music folder in Ubuntu, that mp3 will be in your Music folder in Vista.  Also, if you need to reinstall either Vista or Ubuntu, you won't lose any of your files, since the operating systems are installed to a different partition than your data.

thank you but i already have windows xp pro on, and ubuntu, I just can't dual boot them, I have to put the install disks in to switch between operating systems.  Im trying to find a way to get a boot screen for the two os.  I only plan on using windows for two things, playing games and recording music.

---

### Post by bones16v on 2008-09-21
> **rraj.be said:**
> Could you post the content of 

```
sudo fdisk -l
```

And ```
gedit /boot/grub/menu.lst
```

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe34205af

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5758    46251103+  83  Linux
/dev/sda2   *        5759        9378    29077650    7  HPFS/NTFS
/dev/sda3            9379        9729     2819407+   5  Extended
/dev/sda5            9379        9729     2819376   82  Linux swap / Solaris
```


and 


the second one brings open a file im not sure what you want from that

---

### Post by rraj.be on 2008-09-21
Just post the content of ```
sudo gedit /boot/grub/stage1
```


by that we can find what is the problem for GRUB boot loader to load window's.

---

### Post by bones16v on 2008-09-21
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
# kopt=root=UUID=acbde67e-a308-4273-972b-6f7ede709fe1 ro

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=acbde67e-a308-4273-972b-6f7ede709fe1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=acbde67e-a308-4273-972b-6f7ede709fe1 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

ok thats the first one you told me to do



and for the other one gedit opens but i get this message
> 
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

---

### Post by rraj.be on 2008-09-24
-->

---

### Post by rraj.be on 2008-09-24
Change the contents of /boot/grub/menu.lst as following.

Just copy and replace the whole file with the below content.

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
# kopt=root=UUID=acbde67e-a308-4273-972b-6f7ede709fe1 ro

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=acbde67e-a308-4273-972b-6f7ede709fe1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=acbde67e-a308-4273-972b-6f7ede709fe1 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet



# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows boot loader
root		(hd0,1)
savedefault
makeactive
chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST
```

> ```
Dont forget to Make a copy of the file before modifying it.
```

---

### Post by bones16v on 2009-12-08
> **rraj.be said:**
> Change the contents of /boot/grub/menu.lst as following.

Just copy and replace the whole file with the below content.

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
# kopt=root=UUID=acbde67e-a308-4273-972b-6f7ede709fe1 ro

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=acbde67e-a308-4273-972b-6f7ede709fe1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=acbde67e-a308-4273-972b-6f7ede709fe1 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet



# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows boot loader
root		(hd0,1)
savedefault
makeactive
chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST
```



so how do I do this now that i am on 9.1?

---

### Post by oldfred on 2009-12-08
bones16v, please start a new thread as this one is very old and your issue is not like this since you are now on 9.10. Also include some information about what your problem is and whether you upgraded or did a new, clean install.

---

