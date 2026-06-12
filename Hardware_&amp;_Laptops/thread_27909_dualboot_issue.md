---
title: "dualboot issue"
date: 2005-04-18
forum: Hardware &amp; Laptops
---

### Post by themelvin on 2005-04-18
I have installed Kubuntu 5.04 and it installed Grub boot loader. The report said that another OS was found (Windows XP). When I choose Linux from the boot loader everything is fine. But when I choose windows it says NTLDR IS MISSING, press ctrl+alr+delete to restart.
I can't setup adsl in Kubuntu so I entered the Windows XP Recovery console and wrote fixmbr, now the situation is vice versa. The boot loader doesn't seem to be present anymore, because it goes straight to Windows and I can't choose Linux.

Now, what do I have to do, to "repair" the boot loader? I want the menu in which I select Windows XP or Linux. This is all I want. It would be better if Windows is in the first place, the first OS to load if I don't press a key.

If anybody knows how to do that please write it here, I am desperate.

---

### Post by erkki70 on 2005-04-18
Hi,
Don't be desperate, you'll find here how to get back on tracks restoring Grub and Dual Boot. ;-)

[http://ubuntuguide.org/4.10/index.html#restoregrubmenuafterwindowsinstallation]("http://ubuntuguide.org/4.10/index.html#restoregrubmenuafterwindowsinstallation")
(instructions are from the previous Ubuntu release but works the same for Hoary)
Good luck!

Cheers,
Erkki

---

### Post by themelvin on 2005-04-18
Thank you very much. Will try to do that and post here.

---

### Post by themelvin on 2005-04-18
Hello.

I made a new install and disconnected the second disk. Now it seems to work properly, but can't find teh grub.conf file to insert the lines for Windows XP boot possibility inside of the boot menu.

I have also the problem with ADSL. I can't configure it.
When I write:
apt-get install pppoe
It says that i don't have the root access and it says Permission Denied (code 13).

How can I log in as root? During the installation, I didn't setup the root access mode because it didn't ask me, I only made a new user. 
But when I enter the Control Center and click on the Administrator mode it accepts my password.

If anybody knwos what do I have to do, please tell me.

---

### Post by alastair on 2005-04-18
Try :

sudo apt-get install pppoe

and give YOUR (user) password.

---

### Post by themelvin on 2005-04-18
Ok, will try this.

BBS

---

### Post by themelvin on 2005-04-18
[QUOTE=themelvin]Ok, will try this.

BBS[/QUOTE]
 It says that the package doesn't exist but is reffered by another package.

Would be OK to download this:
[http://www.roaringpenguin.com/penguin/open_source_rp-pppoe.php](http://www.roaringpenguin.com/penguin/open_source_rp-pppoe.php)

Or should I get something else? An how to install this, unzip this inside Linux.

Another thing:
When I try to mount HDA5 it says that only root can do this. So, how can I access the HD partitions?

Thanks

---

### Post by alastair on 2005-04-18
Actually, maybe you already have what you need : "pppoeconf"?

You can check using :

dpkg -l pppoeconf

Then to run : 

sudo pppoeconf

(I do not use PPPoE, so I am not sure)

---

### Post by ToastedToad on 2005-04-19
[QUOTE=themelvin]Hello.

I made a new install and disconnected the second disk. Now it seems to work properly, but can't find teh grub.conf file to insert the lines for Windows XP boot possibility inside of the boot menu.

.[/QUOTE]

sudo gedit /boot/grub/menu.lst

---

### Post by themelvin on 2005-04-19
[QUOTE=ToastedToad]sudo gedit /boot/grub/menu.lst[/QUOTE]
 Alastair thank you very much, now i type from Kubuntu, it worked.

ToastedToad, will try this and repost here.

Thanks a lot

---

### Post by themelvin on 2005-04-19
ToastedToad, I don-t have gedit, the text editor is kate, but when I write
sudo kate /boot/grub/menu.lst
it gives me an error

Error: "/var/tmp/kdecache-marko" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
kate: ERROR: Communication problem with kate, it probably crashed.

When I open the file with Kate manually, selecting it in browser everzthing is OK, except when I try to save the new file it says

The document could not be saved, as it was not possible to write to file:///boot/grub/menu.lst.
Check that you have write access to this file or that enough disk space is available.

What do I have to do

---

### Post by erkki70 on 2005-04-19
Hi,
Try to edit in the terminal or on console with nano, a very simple text editor.
 ```
sudo nano /boot/grub/menu.lst
``` 

Hope this helps.

Cheers,
Erkki

---

### Post by themelvin on 2005-04-19
Hello,

it works, but can't find the number of HD with WIndows XP:

Grub is on (hd0,8 )
Linux (hd0,9)

I entered those lines:
title windowsXP 
 root (hd0,0) 
 makeactive 
 chainloader +1 
 savedefault 

The result is: NTLDR is Missing!

Windows XP are on the other disk, the SATA one. So I think that the numbers or. location must be different from (hd0,0) as I entered.

---

### Post by erkki70 on 2005-04-19
Hi,

Try this:
 ```
fdisk -l
``` 
It will list drives and partitions so you can edit your menu.lst correctly after that.
And check this too:
[http://ubuntuforums.org/showthread.php?t=13036](http://ubuntuforums.org/showthread.php?t=13036)

Hope this helps and good luck.
Cheers,
Erkki

---

### Post by themelvin on 2005-04-19
Thank you very much,  will try this now.

I tried also (sd0,0) but it returns Error 23 cannot parse numbers.

EDIT:

fdisk -l doesn't return anything it just goes on the other line.

but fdisk returns this:
```

marko@senthx:~$ fdisk -l
marko@senthx:~$ fdisk

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...

```

My Windows XP disk is one recognised as SCSI, because is a SATA disk it must be the /dev/sdc.

So, what do I have to write in the menu.lst?

EDIT2:
Now I am root (su -) and it returns this:

```

root@senthx:~ # fdisk -l

Disk /dev/hda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         653     5245191    7  HPFS/NTFS
/dev/hda2             654       20022   155581492+   f  W95 Ext'd (LBA)
/dev/hda5             654       11096    83883366    7  HPFS/NTFS
/dev/hda6           11097       16318    41945683+   7  HPFS/NTFS
/dev/hda7           16319       18929    20972826    b  W95 FAT32
/dev/hda8           18930       19057     1028128+  82  Linux swap / Solaris
/dev/hda9   *       19058       20022     7751331   83  Linux



Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4499    36138186    7  HPFS/NTFS

```

sda: 37GB is My WIndows XP disk.


Thanks for the help

---

### Post by erkki70 on 2005-04-19
Hi,
Could you post your /boot/grub/menu.lst config file?
It might help people to see better what's going wrongly...
Where did you install Grub? 
If installed on the wrong HD this might help you figured out how to correct:
[http://ubuntuforums.org/showthread.php?t=135](http://ubuntuforums.org/showthread.php?t=135)

Cheers,
Erkki

---

### Post by themelvin on 2005-04-19
Hello,
I think that Grub is installed on hda8, but am not sure.

Here is the menu.lst file:

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout  3

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
# title  Windows 95/98/NT/2000
# root  (hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,8)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title  WindowsXP
root  (sd0,0)
makeactive
chainloader +1
savedefault

title  Ubuntu, kernel 2.6.10-5-386 
root  (hd0,8)
kernel  /boot/vmlinuz-2.6.10-5-386 root=/dev/hda9 ro quiet splash
initrd  /boot/initrd.img-2.6.10-5-386
savedefault
boot

title  Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root  (hd0,8)
kernel  /boot/vmlinuz-2.6.10-5-386 root=/dev/hda9 ro single
initrd  /boot/initrd.img-2.6.10-5-386
savedefault
boot

title  Ubuntu, kernel memtest86+ 
root  (hd0,8)
kernel  /boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by themelvin on 2005-04-20
Hi,

I managed to get GRUB working properly, for WIndows XP I inserted these lines:

```

map (hd0) (hd1)
map (hd1) (hd0)
root (hd1,0)
makeactive
chainloader +1 

```

And is working perfectly.

Thanks for the help.

---

### Post by ekravche on 2005-09-03
[QUOTE=themelvin]Hi,

I managed to get GRUB working properly, for WIndows XP I inserted these lines:

```

map (hd0) (hd1)
map (hd1) (hd0)
root (hd1,0)
makeactive
chainloader +1 

```

And is working perfectly.

Thanks for the help.[/QUOTE]

Nice, I will give this a try I was able to set this up before, but am having difficulties right now.

---

### Post by Catachan on 2005-09-03
How would I access programs that are on the Windows Partition? 

That is of course assumeing that it is even possible for Ubuntu to reach through the partition, if it isn't then please just say so.

I would like to be able to use some of my Windows programs in Linux but I want to avoid having duplicates, thanks. . .

---

