---
title: "Uhh... Forgot Bootloader?"
date: 2008-08-05
forum: General Help
---

### Post by customisbetter on 2008-08-05
I recently had a lapse in judgment. I installed XP and created a second partition for ubuntu. I just finished installing ubuntu onto the second partition and now i don't know how to boot back into windows. This is a really stupid situation and has probably been covered but im desperate here. 

Thanks

---

### Post by kellemes on 2008-08-05
> **customisbetter said:**
> I recently had a lapse in judgment. I installed XP and created a second partition for ubuntu. I just finished installing ubuntu onto the second partition and now i don't know how to boot back into windows. This is a really stupid situation and has probably been covered but im desperate here. 

Thanks

Download/Burn/Boot [SuperGrubDisk]("http://supergrub.forjamari.linex.org/") to get back into Windows and/or fix or install Grub (bootloader).

---

### Post by customisbetter on 2008-08-05
yeah i tried the super grub thingy but i am having problems. I am fresh out of cd's and no one has a floppy drive anymore so i am left with the usb option. But when i follow the intructions the terminal gives me an error. 

syntax error near unexpected token `('

thats where i am at...

---

### Post by customisbetter on 2008-08-05
well i used alternate instructions and i got the usb drive to boot but the !win! option doesn't work. so i tried the windows auto version and it automatically loads linux. Im losing my mind here.

---

### Post by customisbetter on 2008-08-05
Bump. I really don't want to re-format everything guys.
i looked at this thread
[http://ubuntuforums.org/showthread.php?t=609548](http://ubuntuforums.org/showthread.php?t=609548)

and i got stuck at the setup (hd0) command. It replies 'invalid device requested'.although it shows my partitions withe the geometry command. WHAT!?!?! so im going to continue smashing my face against the bedpost until i someone can help me.

---

### Post by logos34 on 2008-08-05
try this:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_Windows_entry_into_GRUB_menu](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_Windows_entry_into_GRUB_menu)

---

### Post by customisbetter on 2008-08-05
thanks i tried that but got
'no such file or directory' on the first command.

---

### Post by logos34 on 2008-08-05
unplug any usb drives and run this:

sudo fdisk -l

Post it.

---

### Post by customisbetter on 2008-08-05
Here ya go...

ed@ed-ubuntu:~$ sudo fdisk -1
[sudo] password for ed: 
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
ed@ed-ubuntu:~$

---

### Post by AnarchyCow on 2008-08-05
The command was
```
sudo fdisk -l
```
That's a lowercase "L", not "1", common mistake =].
Now, the response will look something like...
> Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16573   133122591    7  HPFS/NTFS
/dev/sda2           16574       23989    59569020   83  Linux
/dev/sda3           23990       24321     2666790   82  Linux swap / Solaris

Disk /dev/sdb: 61.4 GB, 61471162368 bytes
255 heads, 63 sectors/track, 7473 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7b2d1197

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           2        7473    60018840    f  W95 Ext'd (LBA)
/dev/sdb5               2        7473    60018808+   7  HPFS/NTFS
"sda" is the HDD I boot to, and it's also called (hd0), "sdb" is (hd1) etc...
"sda1" is my main NTFS partition for Windows. so my entry in /boot/grub/menu.lst is:
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1

I had to reinstall grub a lot, but, do you have grub installed right now?
If not, I believe you can
```
sudo apt-get install grub
```


Now, go into a grub shell.
```
sudo grub
```
Now the Terminal should look something like (the same line as your cursor)
> grub>_

Then go ahead and install it to the MBR of the HDD you boot to...
```
root (hd0)
```

now, exit this...
```
quit
```

Then you will need to setup the Windows option in the boot loader..
```
sudo gedit /boot/grub/menu.lst
```
That's a lowercase "L" in .lst, not 1 =]

Then, just set the line like I showed you mine. Only set it for your NTFS partition for windows.

---

### Post by customisbetter on 2008-08-05
ok i have the menu.lst file but what do i replace? I see this...

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

Do i change the groot to my windows partition? (hd0,5) BTW
----------------------------------------------------
EDIT
----------------------------
i pasted this at the end of the menu.lst file, should i save it?

title		Microsoft Windows
rootnoverify	(hd0,5)
savedefault
makeactive
chainloader	+1
--------------------------------------
also, anarchycow, whats with your cpu? seems a little out of place in your signature, no offense.

---

### Post by customisbetter on 2008-08-06
alright the above didn't work. Windows was an option but i got 'invalid device'.

---

### Post by customisbetter on 2008-08-06
Alright i replaced the earlier paste with this...

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title Microsoft Windows XP Professional
root (hd0,5)
savedefault
chainloader +1 

and it says 'starting up' and just hangs there. Im so close...

and sorry for the tri post

here is the product of the fdisk -l command
------------------------------
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00053dcb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1       30400   244187968+   f  W95 Ext'd (LBA)
/dev/sda5            1531        6629    40957686    7  HPFS/NTFS
/dev/sda6            6630       30400   190940526    7  HPFS/NTFS
/dev/sda7               1        1530    12289630+  83  Linux

i believe the sda5 is my windows partition.

---

### Post by customisbetter on 2008-08-06
MY MENU.LST IS EMPTY!!! I'm royally screwed aren't I?

---

### Post by logos34 on 2008-08-06
I'm not sure how windows ended up inside an extended partition, but you can only boot windows on a logical partition if the boot files are located on a primary partition.  So you might want to access windows c:\ (sda6?) from linux, backup whatever you need, and then delete it, shrink the extended, and reinstall windows in the freed space.  You'll have to restore grub afterward, though, and add a windows entry to bottom of menu.lst (whatever happened to it!) with the new 'root' location

---

### Post by /////// on 2008-08-06
zzz I don't know what you did wrong? How come theres a GRUB menu.lst file when you didn't install GRUB? If you don't have anything in the Ubuntu partition, just re-install Ubuntu on that partition again and this time choose to install the GRUB bootloader. If the Windows partition is there, then GRUB should automatically detect it and make the menu.lst for you.

Hope this helps.

---

### Post by customisbetter on 2008-08-06
yeah im just starting over from scratch. im reinstalling xp now.
-------------
ok i installed xp on one partition. i used the ubuntu cd to try to divide the ntfs partition and it won't let me. it only says "guided- use whole disk" 
i am hating life right now. I guess i can't use linux.

---

