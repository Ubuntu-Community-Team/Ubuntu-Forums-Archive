---
title: "Best filesystem for my 500 GB External HD for both linux/windows?"
date: 2007-07-06
forum: Hardware &amp; Laptops
---

### Post by KyleBrandt on 2007-07-06
I am trying to figure out what file system is best for my 500 GB  external HD.  I would like the following:

A Single Partition
Ubuntu and Windows both read and write it natively.

Right now I am using NTFS with NTFS-3g, it says it is mounted as fuseblk, but the high processor usage as well as the experimental warnings make me want to seek an alternative.  I know I can read/write ext3 in windows, but I had to install a different driver for that, but maybe that is a better option?

---

### Post by mytwobears on 2007-07-07
Windows and Linux/Ubuntu both read and write to the FAT32 file system also.  The drawback is windows won't write a file bigger than 4GB to it.

---

### Post by bigken on 2007-07-07
use ext2 and install [this]("http://www.fs-driver.org/") so windows has read/write

---

### Post by jrusso2 on 2007-07-07
I would say to use NTFS and then install NTFS 3g in ubuntu so you can write to it

---

### Post by bigken on 2007-07-07
> **jrusso2 said:**
> I would say to use NTFS and then install NTFS 3g in ubuntu so you can write to it

ah thats because your faith still lies in windows where as mine lies in linux ;)

---

### Post by KyleBrandt on 2007-07-07
Thanks for your advice guys, I am going with ext3, and using the driver from windows to read it.  I am also going to try to shrink my windows parition to almost nothing, and take care of my few windows needs through vmware.

---

### Post by marsmissionaries on 2007-07-07
i reccoment fat32.

---

### Post by bigken on 2007-07-07
> **marsmissionaries said:**
> i reccoment fat32.

but fat32 cant handle anything over 4gig

---

### Post by strabes on 2007-07-07
and fat32's permissions are screwey and it has problems with two-extension files like tar.gz in my experience.

---

### Post by Depressed Man on 2007-07-07
Tis a good question as I have a 400 GB external HDD myself that's in NTFS format right now. But it holds files I hold dear (pictures that are memories). So I'd want a reliable file system as well that's not likely to screw up and require a format.

---

### Post by uputer on 2007-07-30
I would like to find a good system for transferring files between Windows and Linux myself.  

Could anyone comment on these methods or suggest another?:

1) FAT32

2) This one:  [http://www.fs-driver.org/](http://www.fs-driver.org/)

3) Samba

4) use NTFS and then install NTFS 3g

5) SFTP? WinSCP?  [http://www.linux.com/feature/62254](http://www.linux.com/feature/62254)

---

### Post by stchman on 2007-07-30
> **KyleBrandt said:**
> I am trying to figure out what file system is best for my 500 GB  external HD.  I would like the following:

A Single Partition
Ubuntu and Windows both read and write it natively.

Right now I am using NTFS with NTFS-3g, it says it is mounted as fuseblk, but the high processor usage as well as the experimental warnings make me want to seek an alternative.  I know I can read/write ext3 in windows, but I had to install a different driver for that, but maybe that is a better option?

What kind of partition sizes are you looking at?

I recommend FAT32 as both XP and Linux can read/write to them no problem.  There is the 4GB file size limitation for FAT32 though.

---

### Post by uputer on 2007-07-31
> **KyleBrandt said:**
> I know I can read/write ext3 in windows, but I had to install a different driver for that......Thanks for your advice guys, I am going with ext3, and using the driver from windows to read it. 
Btw, I am confused.   What driver are you talking about?   He's not talking about that fs-driver program, is he?   Can someone let me know what driver for Windows reads ext3 files and I assume you can only read the files, not write?   Or can you?   Thanks.  Yeah, okay, I'm a noob.   So sue me. ;-)

---

### Post by Bachstelze on 2007-07-31
Yes, you can read and write to your ext3 parititons in windows :

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by clblanchard on 2007-07-31
> **bigken said:**
> use ext2 and install [this]("http://www.fs-driver.org/") so windows has read/write

No, you still use ext3 for the journaling capabilities.  Windows will still be able to write to it because ext3 is just ext2 with a journal.  I know because I use the same program you recommend.

---

### Post by uputer on 2007-07-31
Well, how do you find it working for you?   It's only one guy's program.   There is no support group, is there?   What is the typical experience with it?

---

### Post by pavallokazzo on 2008-01-16
Same problem here
I've buyed an external usb adaptor or internal hd and have to choose what FS to use...
That's my point:
- the HDs will be used as archive units
- some of the HDs were presenting badblocks problem. I have recovered them with badblocks utility and they now seem safe (many dd in read and write on an ext3 unique partition produced no error)... Note that that is a MAJOR point
- I WANT(!) the possibility to plug the device in a laptop or desktop running windows without have to touch install or do anything... plug & play!

So that's what:
- ext3 would be perfect but ain't got native support in windows... :cry: so I have to put it away
- fat32 it's so-so as it ain't got journaling, can't deal with badblocks (as far as I know) and limit file size to 4 gb, plus they say it can give random bad problems
- ntfs: what about that? it should have journaling and sure exceed the 4 gb fat limit... but they say it got fragmentation problem, resources consumption and many minor issues I read somewhere... plus, ntfs-3g is really safe? and what about dealing with badblocks???

Wish you're help

---

### Post by pavallokazzo on 2008-01-18
bump

---

