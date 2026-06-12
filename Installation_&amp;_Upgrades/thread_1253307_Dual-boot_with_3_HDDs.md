---
title: "Dual-boot with 3 HDDs"
date: 2009-08-29
forum: Installation &amp; Upgrades
---

### Post by Thesord on 2009-08-29
I've used Ubuntu for some time on another system, but on this one I have multiple hdds. I'm kind of a newbie here as I pretty much used the automated process in the past.

I have 3 hdds. One of them had XP installed, the other was ntfs holding data and I chose the third one to install Ubuntu 9.04 as well as GRUB (formatted the whole hdd). I then changed bios boot priority so that the hdd with grub would boot first.

Ubuntu boots fine but it fails to boot XP through grub.

I checked the /boot/grub/menu.lst file to see how the XP entry is:
(it was created with hd1,0 automatically)
```

title		Microsoft Windows XP Professional
rootnoverify	(hd1,0)
savedefault
chainloader	+1
```

I have read that XP can't boot unless it is in the first hdd so I need to add the mapping commands to get the desired behaviour:

```
grub>map (hd0) (hd1)
grub>map (hd1) (hd0)

```
I have two problems here.

I don't know which hdd is the one that has Windows XP (that is, if hd1,0 is the right thing). When I tried to boot with the entry above I got grub error 13 "Invalid or unsupported executable format".

Secondly I also don't know in what order I need to add the mapping commands to the XP entry on the meny.lst.

My fdisk -l output is the following:

(80.0 GB is XP, 250.0 GB ntfs is the data one)

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf7f7f7f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9a99c226

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14402   115684033+  83  Linux
/dev/sdb2           14403       15017     4939987+   5  Extended
/dev/sdb5           14403       15017     4939956   82  Linux swap / Solaris

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00e5a77f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30400   244187968+   7  HPFS/NTFS
```

Appreciate any help :)

---

### Post by tgeer43 on 2009-08-29
Not a complete answer but according to your fdisk output:

/dev/sda1 (hd0) is 80GB NTFS (Windows)
/dev/sdb1 (hd1) is 123.5GB Linux (Ubuntu)
/dev/sdc1 (hd2) is 250GB NTFS (data)

tgeer

---

### Post by tal007 on 2009-08-30
Be careful before you take any further steps. It looks like you have boot sectors in three separate drive partitions. You can see the boot flags.
It looks like /dev/sdc1 has the grub loader given the size next to it and also noticed a boot flag next to it. Grub boot loader requires little over 32k or something.


/dev/sda1  looks like has Xp boot loader

/dev/sdb1  looks like has the Linux boot loader

/dev/sdc1  looks like has the GRUB boot loader

---

### Post by presence1960 on 2009-08-30
when adding the entry for Windows in menu.lst you need to know the boot order of your disks in BIOS. Example if the windows disk boots 2nd after the Ubuntu disk your entry would be:

```
title          Windows
rootnoverify   (hd1,0)
map            (hd0) (hd1)
map            (hd1) (hd0)
chainloader    +1 

```
when using the root or rootnoverify to ID disks & partitions it is the order in BIOS that you want to use because that is the actual order of hard disk booting. Sometimes fdisk reads the order of disks differently.

If windows is on the 3rd disk to boot your entry would look like this:

```
title          Windows
rootnoverify   (hd2,0)
map            (hd0) (hd2)
map            (hd2) (hd0)
chainloader    +1 

```

---

### Post by tal007 on 2009-08-30
What I have read in a posted article on the internet - Linux and GRUB do not view the same way.

If you have 3 hard drives, Linux will view it this way -

 1st Hard Drive as /dev/sda1

 2nd Hard Drive as /dev/sdb1

 3rd Hard Drive as /dev/sdc1



Grub views it differently.
From Grub's perspective this is how it will look like -

1st   Hard Drive    hd0

2nd   Hard Drive    hd1

3rd   Hard Drive    hd2


So, if we take this logical view, according to your display hd0
has XP on it, hd1 has Ubuntu on it and hd2 has GRUB on it.


 
This is how mapping will look like.

/dev/sda1      hd0      XP

/dev/sdb1      hd1      Ubuntu

/dev/sdc1      hd2      GRUB

---

### Post by presence1960 on 2009-08-30
since you have 3 disks in your machine and we really don't know where you installed GRUB do this:

Let's get a better look at your setup. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. This will give us a clear picture of your setup so we can give you the exact entries for windows in menu.lst.

---

### Post by presence1960 on 2009-08-30
> **tal007 said:**
> What I have read in a posted article on the internet - Linux and GRUB do not view the same way.

If you have 3 hard drives, Linux will view it this way -

 1st Hard Drive as /dev/sda1

 2nd Hard Drive as /dev/sdb1

 3rd Hard Drive as /dev/sdc1



Grub views it differently.
From Grub's perspective this is how it will look like -

1st   Hard Drive    hd0

2nd   Hard Drive    hd1

3rd   Hard Drive    hd2


So, if we take this logical view, according to your display hd0
has XP on it, hd1 has Ubuntu on it and hd2 has GRUB on it.


 
This is how mapping will look like.

/dev/sda1      hd0      XP

/dev/sdb1      hd1      Ubuntu

/dev/sdc1      hd2      GRUB
Not necessarily true if you are referring to mapping in menu.lst for the windows entry. When using (hdx,y) in menu.lst to designate disks & partitions you must use the actual order of the disks in the BIOS boot order. Why?

Because that is the actual order of the disks when you turn on your machine. Sometimes fdisk reports a different order than the actual order of disk booting. The bottom line is regardless of what fdisk reports the BIOS controls the order of booting hard disks and that is the actual order in the system.

This discrepancy is probably why the devs went with UUID in Jaunty for Ubuntu's partitions. But for chainloading we still use root (hdx,y) or rootnoverify (hdx,y). In these cases you must use BIOS order of disks to determine which is (hd0), (hd1), (hd2), etc.

---

### Post by Thesord on 2009-08-30
I checked my bios hard disk boot priority. The 125 GB hdd with Ubuntu and GRUB is the first. The 80 GB hdd with XP is the second (therefore hdd1,0 is supposed to be it according to Presence1960) and the 250 GB one with data is third.

```

title		Microsoft Windows XP Professional
rootnoverify   (hd1,0)
map            (hd0) (hd1)
map            (hd1) (hd1)
chainloader    +1
```

Given that, the above should've worked (it just stood on loading... and didn't access the disk), according to the bios boot priority for hdds.

However, if I go by tal007, should I remove the mapping operations and set rootnoverify to (hd0,0)?

---

### Post by presence1960 on 2009-08-30
```
title		Microsoft Windows XP Professional
rootnoverify   (hd1,0)
map            (hd0) (hd1)
map            (hd1) [COLOR="Red"](hd1)[/COLOR]
chainloader    +1
```

the entry in red should be (hd0)

P.S. that has been posted for 6 hours, I find it hard to believe no one caught that error!

---

### Post by Thesord on 2009-09-01
You'd be surprised... Well it did work, thanks for the help guys!

---

### Post by presence1960 on 2009-09-01
> **Thesord said:**
> You'd be surprised... Well it did work, thanks for the help guys!

Great!! Enjoy Ubuntu.

---

