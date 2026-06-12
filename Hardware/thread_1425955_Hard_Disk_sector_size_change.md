---
title: "Hard Disk sector size change"
date: 2010-03-09
forum: Hardware
---

### Post by Manyette on 2010-03-09
Based on the little I know about Ubuntu, I believe that the coming change in Hard Drive sector sizes from 512 to 4K will have little or no effect on our favorite OS.  If I am making a rash assumption, would someone please straighten me out, and tell me what the ramifications of this change will be?  Thanks all.

---

### Post by adam814 on 2010-03-09
Well, from everything I've read on the topic either way it'll work out.  AFAIK these drives with 4K sector sizes aren't very common (if even commercially available right now).  They're expected to "emulate" the 512K sector size for machines that can't deal with them.

So if somehow support for this has slipped past the Linux kernel developers (I highly doubt it, hard disks are pretty crucial for enterprise) it should still be OK until they can be supported natively.

---

### Post by Manyette on 2010-03-09
> **adam814 said:**
> Well, from everything I've read on the topic either way it'll work out.  AFAIK these drives with 4K sector sizes aren't very common (if even commercially available right now).  They're expected to "emulate" the 512K sector size for machines that can't deal with them.

So if somehow support for this has slipped past the Linux kernel developers (I highly doubt it, hard disks are pretty crucial for enterprise) it should still be OK until they can be supported natively.

What I have read says that the 4K Sector size is mandated beginning next year.  Most warnings on the subject are concerned with Windoze XP.  I'm just trying to decided if I should worry about purchasing a drive now that will not have a future problem.  I agree that it's unlikely that the kernel developers have missed this.  Mostly I was wondering if the Ubuntu format funtion on install can handle this. AFAIK, it is possible for the install to do this without problem, but I also know how little I know!

---

### Post by adam814 on 2010-03-10
For what it's worth the man page for fdisk on mine (Lucid Alpha 3) has an option to specify the sector size of the block device when making partitions, but suggests this is only for older kernels as newer ones will know the physical block size.

That's encouraging, even though I think the installer uses parted (since users may want to resize other OS partitions to make space for Ubuntu).  Since parted is "more advanced" than fdisk I would think a sufficiently new version wouldn't have any problem.

If I'm not mistaken the worst-case would be Ubuntu accessing the new drives using a 512K logical sector size and dealing with the associated performance hit (not unlike SSDs with block sizes smaller than the physical blocks).

---

### Post by leg on 2010-03-10
Apparently the Linux kernel has been prepared [since 2009]("http://news.bbc.co.uk/1/hi/technology/8557144.stm")

---

### Post by cascade9 on 2010-03-10
Been talking about this on a different thread, from a slighty differentstart point. Thread here (most of this imformation is also on the thread, so its just for the sake of disclosure I'm even putting this info up)- 
 
 [http://ubuntuforums.org/showthread.php?p=8941622#post8941622](http://ubuntuforums.org/showthread.php?p=8941622#post8941622)
 
 > **adam814 said:**
> Well, from everything I've read on the topic either way it'll work out. AFAIK these drives with 4K sector sizes aren't very common (if even commercially available right now). They're expected to "emulate" the 512K sector size for machines that can't deal with them.
 
 They are out WD Green Power EARS drives are the 1st 4K sector HDDs to market, and avaible right now. 
 
 There is a jumper on the EARS drives you can set to "achive full performance with XP on a single partiton", if you want to have multipule partitions on a EARS drive with XP you will need to use the align tool (WD Advanced Format Utility)- 
 
 [http://support.wdc.com/product/download.asp?groupid=618&lang=en](http://support.wdc.com/product/download.asp?groupid=618&lang=en)
 
 Drive label- 
 
 [http://blog.fosketts.net/wp-content/uploads/2009/12/WD10EARS.png](http://blog.fosketts.net/wp-content/uploads/2009/12/WD10EARS.png)

> **adam814 said:**
> For what it's worth the man page for fdisk on mine (Lucid Alpha 3) has an option to specify the sector size of the block device when making partitions, but suggests this is only for older kernels as newer ones will know the physical block size.

That's encouraging, even though I think the installer uses parted (since users may want to resize other OS partitions to make space for Ubuntu). Since parted is "more advanced" than fdisk I would think a sufficiently new version wouldn't have any problem.

If I'm not mistaken the worst-case would be Ubuntu accessing the new drives using a 512K logical sector size and dealing with the associated performance hit (not unlike SSDs with block sizes smaller than the physical blocks).

From what I saw here, parted migth be a better choice- 

[http://www.osnews.com/story/22872/Linux_Not_Fully_Prepared_for_4096-Byte_Sector_Hard_Drives](http://www.osnews.com/story/22872/Linux_Not_Fully_Prepared_for_4096-Byte_Sector_Hard_Drives)
 
I'm not 100% if you even need to use the "--align optimal" option with parted, or if it does it automatically. *looks sheepish* I perfer to let other people figure this stuff out for me, learning from others mistakes is a lot less stressful. 

BTW, the performance hit from unaligned sectos with the new drives is shockly bad. See link above and here- 

[http://www.xbitlabs.com/articles/storage/display/1tb-hdd-roundup-3_13.html](http://www.xbitlabs.com/articles/storage/display/1tb-hdd-roundup-3_13.html)

[QUOTE=Manyette;8943395] I'm just trying to decided if I should worry about purchasing a drive now that will not have a future problem. /QUOTE]

You should be fine for a fair while yet. The HDD manufacturers are going to move, slowly to 4K sectors (AFAIK they have to to get past the 2TB limit) but 512B sector drives are going to be around for a long time yet. Even if you do get a 4K sector drive you can still use the jumper or the align tool with Windows XP use. AFAIK you shouldnt use BOTH, just one or the other.

---

### Post by Manyette on 2010-03-10
Hi adam814 and leg. thanks for the replies.  Adam that was good info, and thanks.  And leg, I am really embarrassed, because the article you referred me to was the exact same one that got me on this subject, and I totally missed the linux reference.  Too busy with the details to see the whole pictures I guess.  So to both of you, many thanks.

---

### Post by Manyette on 2010-03-10
Thanks to Cascade 9 as well.  All info appreciated.

---

