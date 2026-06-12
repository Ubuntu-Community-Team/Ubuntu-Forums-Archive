---
title: "Windows only sees 126 of 250 gigs on hdd!!!!!"
date: 2009-03-22
forum: Hardware
---

### Post by ChodeOfDoom on 2009-03-22
I just got a WD scorpio blue hdd for my toshiba satellite l15 s104 laptop.  When I installed windows, however, it didn't recognize all of my storage!  How can I get back that space so I can use it for windows or to multiboot or whatever???

---

### Post by cybergalvez on 2009-03-22
What does disk manager report? are you sure the entire drive was formated correctly?

---

### Post by ChodeOfDoom on 2009-03-22
Ehh... whassa disk manager?  And how so I get to it?  Btw, I put in an old ms dos disk and it said that the whole disk was full.  Ima go pop in a ubuntu 8.1 live and see if it recognizes the whole disk.

---

### Post by Potters Son on 2009-03-22
Is the missing storage ext3 (Linux system/home partition(s))? If so, of course Windows won't read it. You'd need another program to install a driver for ext3, such as Ext2IFS ([http://sourceforge.net/projects/freshmeat_ext2ifs/]("http://sourceforge.net/projects/freshmeat_ext2ifs/")).

---

### Post by ChodeOfDoom on 2009-03-22
> **ChodeOfDoom said:**
> Ehh... whassa disk manager?  And how so I get to it?  Btw, I put in an old ms dos disk and it said that the whole disk was full.  Ima go pop in a ubuntu 8.1 live and see if it recognizes the whole disk.


So I found disk manGement and it says that I am using the whole disk.  But I am not..

---

### Post by lisati on 2009-03-22
The difference between 126 & 250 seems a little much to be accounted for by the diffeent interpretations of Gb (1000Mb or 1024Mb, that sort of thing).

(In between me reading the original post & me clicking "reply" some of the ideas I had seem to have been addressed, e.g. extra hidden partitions or hidden files put in by Windows.)

---

### Post by cybergalvez on 2009-03-22
> **ChodeOfDoom said:**
> So I found disk manGement and it says that I am using the whole disk.  But I am not..

I would look at the disk partitions with gparted jut to make sure its partitioned correctly.  It on the ubuntu live disk of you've got it, and if you don't its nice to have anyway

---

### Post by ChodeOfDoom on 2009-03-22
Well, sure enough, the live cd sees the whole thing.  You say that gparted it on the cd?  I shall use it, or at least try to.EDIT: where is it on the dumb cd????

---

### Post by Potters Son on 2009-03-22
System menu -> Administration -> Partition Editor.

From here, you can view/edit the disk's exact partition structure.

If you find the need to delete partitions, keep in mind that doing so WILL erase all the data on the partition. I advise you to make whatever backups necessary.

---

### Post by ChodeOfDoom on 2009-03-22
What if I want to run it from inside of windows?

---

### Post by ChodeOfDoom on 2009-03-22
Well I used the ISO from gparteds website and I resized my windows partition.  It works fine, but I would like to know how to make a new partition for red hat.

---

### Post by cybergalvez on 2009-03-22
> **ChodeOfDoom said:**
> Well I used the ISO from gparteds website and I resized my windows partition.  It works fine, but I would like to know how to make a new partition for red hat.

make some space for it by shrinking your windows partition and then just install red hat in the empty space

---

### Post by Potters Son on 2009-03-22
What, gParted? I have no idea. I don't think that there is a windows port (it was written by the GNOME project, which develops for linux). I don't think that you even WOULD want to run it in anything other than the LiveCD environment, where the hard drives you're running aren't mounted. It's like making a bed when you're still on it; it's extremely difficult to partition a disk from within the operating system which uses it.

So, I think that you should do recon on your HD from within gparted, go back and back up windows (if necessary; if you're growing an existing partition *this isn't needed*), and then do your operations from the LiveCD.

I always keep a LiveCD with my laptop, just for backup. I think it's simply good practice to do so.

Edit: never mind, didn't see the second page.

---

### Post by millsy_c on 2009-03-22
What service pack is the xp install? Early versions of xp could not see larger than around that amount iirc

---

### Post by novafluxx on 2009-03-23
Certain versions of Windows XP cannot see more than 126GB. I believe that with service pack 2 or 3 this is no longer an issue, but I'm not sure.

---

