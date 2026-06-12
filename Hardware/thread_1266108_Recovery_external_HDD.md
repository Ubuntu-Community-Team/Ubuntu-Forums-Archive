---
title: "Recovery external HDD"
date: 2009-09-14
forum: Hardware
---

### Post by JacobK on 2009-09-14
I tried to use an external HDD which was always used on an Imac on a PC. On other PC's this did work out, but this time my laptop said everything was allright, but the HDD wasn't in my computer.

I went to Disk Management, initialized the disk etc, but then it went wrong: or I wasn't paying attention, or Windows didn't say clearly what was happening, but Windows started to format the disk. I stopped it rightaway, so this was just for a few seconds.

Now I can't read the HDD anymore on Mac, PC and Ubuntu, and I do want this without losing all data. How can I do this on Ubuntu? A step-by-step-tutorial would be cool, for I don't have any confidence in myself at this moment. :P

I'm working on Ubuntu 9.04
 


In the attachment you'll see a screenshot of the disk in Gparted.

---

### Post by earthpigg on 2009-09-14
```
sudo apt-get install testdisk
```

read up on testdisk and photorec.

```
man testdisk
man photorec
```

i suggest using photorec first, then testdisk.

ensure you have photorec send the recovered files to a different physical drive than the one you are working on.

---

### Post by JacobK on 2009-09-16
I used testdisk, and I now want to write the partition table to the disk, but I get this:

```
Function write_part_mac not implemented
Use pdisk to recreate the missing partition
using values displayed by TestDisk
```

What can I do?

---

### Post by ubongo2008 on 2009-09-16
recovering that one will take ages because i think that the section of your disk is gone or corrupted which holds the information of which block/sector belongs to which file it also holds stuff like file name, rights, type ... and so on. So i would guess that you need an application which preforms "RAW"-data recovering (RAW = read file-system independet sector by sector and try to detect the file-type and reassemble the file)  

My best bet would be to test some commercial recovering tools aviable and then choose the best one. just test them let them search for files but don't let them alter anything on that disk. if you have found one which works good for you  then you may start to recover. 

Well if that fails you may want to give your disk to an professional recovery institution they can recover everything even in case of an fire but that will be pretty expensive (400 $ and more) so it depends on how important the data on that disk is for you.

Edit: if you have an second disk which can hold all the data of your defect one then i would recommend that you do an sector-by-sector backup with  with clonezilla ([http://clonezilla.org/](http://clonezilla.org/)) or something similar first because things can get worse if you write on that disk. so getting an backup is the best thing to do first.

oh you can also use dd to make an 1 to 1 clone of your defect disk
if you want to use clonezilla (its linux based and for free) have a look here [http://clonezilla.org/download/sourceforge/](http://clonezilla.org/download/sourceforge/)

---

### Post by JacobK on 2009-09-16
Isn't there any way to rewrite the partition table for hfs using Ubuntu?

---

