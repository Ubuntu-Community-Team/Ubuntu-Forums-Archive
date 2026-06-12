---
title: "Which file format for media storage (external)"
date: 2012-12-28
forum: Hardware
---

### Post by Mr_Vile on 2012-12-28
Hi all,

The situation;
I've just removed & enclosed an old laptop 2.5 SATA hard disk (320GB) which I plan on using for storing media (mainly mp3's, potentially some images, nothing over 4GB though). I'm also planning to use it as portable storage (for those situation where a friend says 'bring some music!' to a party or whatever - usually doesn't happen twice with my taste in music :D).

The question;
Which filesystem should I use bearing in mind the portability issue? I only have a limited knowledge of filesystems and google hasn't really thrown up anything specific. At the moment NTFS seems like where I need to go, but I know there's other filesystems that would suit my needs, I just don't know whether any are particularly preferable, so if someone has any suggestions (+ reasoning, to indulge my thirst for knowledge) it would be great to hear.

Many thanks,
MV

---

### Post by TOMBSTONEV2 on 2012-12-28
FAT32 would work well for this purpose, think of flash drives, those are formatted in FAT32. FAT32 goes cross platform quite nicely.

---

### Post by sammiev on 2012-12-28
I would use and do use Fat32 as well. :)

---

### Post by gnush on 2012-12-28
FAT32 is okay if you're not planning on storing files that are bigger than 32 GB, I suppose. I'd personally go for NTFS or ext3 though, because it's a hard drive.

---

### Post by Bucky Ball on 2012-12-28
FAT is not a good option. It has limited capacities (max file size) which is why USB dongles come formatted with it; a throw back to when they were much smaller capacity so FAT was suitable and adequate. Not the best for storing media.

You don't mention anything about Ubuntu or Linux in this question, but as this is a Linux forum, I am presuming you are wanting to use this external drive between Ubuntu and any other OS.

NTFS it is ...

@ gnush: 4Gb for FAT rather than 32Gb. Ext3 (or EXT anything) is no good as a Win machine doesn't recognise it, and that is likely what the friends will be running ...

---

### Post by haqking on 2012-12-28
> **gnush said:**
> FAT32 is okay if you're not planning on storing files that are bigger than 32 GB, I suppose. I'd personally go for NTFS or ext3 though, because it's a hard drive.

File size limit on FAT32 is 4GB not 32GB.

Also ext is no good for OP a they want to take it to other computers which may or may not be Windows.

to OP I would go with NTFS but it is upto you, FAT32 is ok except it doesnt tend to handle long filenames very well.

Peace

---

### Post by ahallubuntu on 2012-12-28
NTFS for sure.  It's very reliable in Linux - I've used it for many years.  I've never had any sort of reliability issue (knock on wood).  The only issue I've found with NTFS is very large files (1GB or larger) - they can take a very long time.  And the fuse driver can eat a lot of your CPU accessing NTFS partitions.

FAT32 is not a great choice just because of the file size limitation.  There is a fake 32GB partition size limitation for FAT32, but that's only self-imposed by Windows itself.  It's not real.  I've made very large FAT32 partitions before without using the Windows Disk Management and they have worked fine even in Windows.  Still, I prefer NTFS.  I'd hate to run into a file size limitation!

---

### Post by Mr_Vile on 2012-12-28
Wow guys, thanks for the speedy responses, many thanks!

@Bucky Ball,
Thanks for the response, sorry I should have clarified, I use Ubuntu - so yes I was referring to cross-OS

@haqking
Thanks - I hadn't thought about filenames

As an aside, is that where messy filenames with ~'s in come from?

---

### Post by haqking on 2012-12-29
> **Mr_Vile said:**
> Wow guys, thanks for the speedy responses, many thanks!

@Bucky Ball,
Thanks for the response, sorry I should have clarified, I use Ubuntu - so yes I was referring to cross-OS

@haqking
Thanks - I hadn't thought about filenames

As an aside, is that where messy filenames with ~'s in come from?

yes it truncates names it cant handle and appends a tilde ~

Peace

---

### Post by TOMBSTONEV2 on 2012-12-30
After reviewing this, and other documentation it does seem like NTFS is the way to go. In the future this is what I am going to choose. I learn a lot from these forums, and I still have much much more to learn.

---

### Post by Bucky Ball on 2012-12-31
> **TOMBSTONEV2 said:**
>  I learn a lot from these forums, and I still have much much more to learn.


That's what we're here for and we all learn something on a regular basis! Enjoy and peace to you. ;)

(Look up the meaning of Ubuntu: What I know, you know, in a nutshell ... knowledge belongs to everyone.)

---

### Post by fdrake on 2012-12-31
I just want to add that when you choose to format the disk into NTFS , make sure that you select the slow type not the quick one, You can save yourself some errors and failurs in the future..... just keep:lolflag:ing you on your toes! :D

---

