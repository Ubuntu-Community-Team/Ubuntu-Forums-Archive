---
title: "Linux Newbie Install Questions"
date: 2005-12-31
forum: Installation &amp; Upgrades
---

### Post by GregM on 2005-12-31
New to Linux, but am an experienced (or is it abused?) MS WIN 2k admin. Just installed Ubuntu 5.1 on my home system and have a couple of questions:

1. Installed Ubuntu to a different physical drive than my win2k pro install. Looks like GRUB didn't see my win2k install...result: no dual-boot. Any recommendations on how to fix?

2. My Soundblaster Live 5.1 card doesn't seem to be working. Any hints?

3. Webcam...webcam... I run screaming in the night, webcam. I have a new Logitech 5000 Pro. Doesn't appear to be working either. Can't seem to find drivers for it. Any ideas?

Thanks in advance for any help you might provide.

Happy New Year,
Greg

---

### Post by GregM on 2005-12-31
Ok...solved the Soundblaster Live 5.1 problem.

---

### Post by inhetep on 2005-12-31
I 've got only a suggestion to question 1

U might need to modifiy the menu.lst.

First find out what the partition of your win system is?
i.e. 

```
sudo fdisk -l /dev/hda 
```

Should be the one formated with NTFS/HPFS.

on my computer it looks like this:

>    
Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/hda1   *           1         855     6867756    7  HPFS/NTFS
/dev/hda2             856         889      273105    6  FAT16
/dev/hda3             890         915      208845   83  Linux


So it would be /dev/hda1
can be different on your machine

Now open the file menu.lst, it contains your grub menu. You will find it in the directory /boot/grub

```

cd /boot/grub
/
```

Now we will make a backup just in case.

```
sudo cp menu.lst menu.backup
```

Now you need to edit the existing file. Open the file with the editor of your choice. Assuming u use Gnome

```
sudo gedit menu.lst
```

It's usually self explanatory.

But if you scroll down you will find entries like this, mostlikely without the windows part:

> 
title		Ubuntu, kernel 2.6.13-ck8 
root		(hd0,2)
kernel		/vmlinuz-2.6.13-ck8 root=/dev/hda5 ro nolapic noapic quiet
initrd		/initrd.img-2.6.13-ck8
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-k7 (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.12-10-k7 root=/dev/hda5 ro nolapic noapic single
initrd		/initrd.img-2.6.12-10-k7
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		FreeDOS
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


 
Now look at the part root for the windows system:
It is stating 

> 
root		(hd0,0)


Which means look for the first harddrive and the first partition.
As u see linux starts counting with zero.
Now you need to adapt your entry depending on th outcome of  the fdisk command.

i.e. if your win system drive is /dev/hda2 then your root entry woud be

```
root (hd0,1)
```

if your system lies on hdb1 also another physical drive

then it would look like this

```
root (hd1,0)
```

So you need to modify the entry accordingly.

I hope this is somewhat clear. :confused: 

Otherwise you might want to post the output of your fdisk query.

For your other problems, did you install the restricted modules for your kernel?

---

### Post by GregM on 2005-12-31
Thanks for the info: below is the output from running the fdisk command:

Disk /dev/hda: 6480 MB, 6480101376 bytes
255 heads, 63 sectors/track, 787 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         751     6032376   83  Linux
/dev/hda2             752         787      289170    5  Extended
/dev/hda5             752         787      289138+  82  Linux swap / Solaris

Nothing immediately obvious here that would indicated WIN2K pro. My primary drive is the drive where LINUX is installed (a formerly unformatted drive, C:\ on my win2k install). My D:\ drive (slave) was my win2k install with 3 partions (OS, Applications, Data). I thought I read somwhere that it might be necessary to logically reassign drive numbers (0=1, 1=0)... has anyone seen this?

Greg

---

### Post by vasudevank on 2005-12-31
you need to put the ones with zeros for grub.conf nothing else

---

### Post by inhetep on 2005-12-31
Since your win system is on your second drive. U need  to run 

```
sudo fdisk -l /dev/hdb
```

and you should find your windows system.

I guess the entry in your menu.lst might be.

```

title Microsoft Windows 
root (hd1,0)
savedefault
makeactive
chainloader +1
```

Which means that windows system is on /dev/hdb1.
If notpost the outputof the above fdisk query.

vasudevank please elaborate your statement.:confused:

---

### Post by GregM on 2006-01-02
Thanks. Will try the entries you suggested. FYI, here's the fdisk output:

Disk /dev/hdb: 40.9 GB, 40981118976 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1            4214        4981     6168960    f  W95 Ext'd (LBA)
/dev/hdb2             262        2173    15358140    7  HPFS/NTFS
/dev/hdb3            2174        4213    16386300    7  HPFS/NTFS
/dev/hdb5            4214        4981     6168928+   7  HPFS/NTFS

Thanks again for the help. I really want to learn to love LINUX :)

Greg

---

### Post by be11o on 2006-01-03
I am running into the same issues with my Soundblaster Live! card. How did you amend the problem on your machine?

---

### Post by GregM on 2006-01-03
Re: my soundblaster Live card; Turns out it was identified during install... it just didn't load it as the default audio processor. 

System-Sound
In the sound preferences dialogue box I had to assign the correct default audio card.

Good luck...

Greg

---

