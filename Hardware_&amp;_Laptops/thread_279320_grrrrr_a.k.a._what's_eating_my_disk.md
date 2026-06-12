---
title: "grrrrr a.k.a. what's eating my disk?"
date: 2006-10-17
forum: Hardware &amp; Laptops
---

### Post by zekopeko on 2006-10-17
hi,

i have a 320 GB IDE seagate disk in a ICYBOX USB enclosure.
the system finds the disk with no problems. i used gparted to format it and this is where the problems started.

after formating with gparted (disklabel:msdos , FS ext3 ) showed that 4.8 GB are in use. hmmmm....
then i mount it with

```
sudo mount /dev/sda1 /media/Biggy
```

after that nautilus shows that there are 278 GB free.
i know that 320 is actually around 298 GB so the question is what is eating my HDD. i'm currently formating to NTFS it to see if it has bad sector because i'm more familiar with win HDD tools.

is it going to be a problem if i foramt it a few dozent time before it works? those so much formating mess the disk or is it like normal write operation?
and what is eating a crap load of my new disk? 
i feal like ](*,) after trying to find the answer in vain.
only thing i want is a storage device for my movies/series/pictures/music.

i want to convert the rest of my HDD's to ext3 or something similar and stop messing with windows.

---

### Post by louieb on 2006-10-17
If I remember right the EXT3 file system reserves some room for journaling.

---

### Post by taurus on 2006-10-17
> **louieb said:**
> If I remember right the EXT3 file system reserves some room for journaling.
5%, I believe.

---

### Post by Predius on 2006-10-17
Not only that, but many HDDs are actually overrepresented, the buyed being told that the disk is bigger than it actually is.

---

### Post by Quintin Riis on 2006-10-18
This doesn't really seem too out of the ordinary.  Any modern filesystem is going to have a bit of overhead.

---

### Post by discord on 2006-10-18
could it be your girlfriend?

---

### Post by zekopeko on 2006-10-18
> **louieb said:**
> If I remember right the EXT3 file system reserves some room for journaling.
> **taurus said:**
> 5%, I believe.

googling this i found that the jorunal isn't big. some 128 mg, probably depending on the size of the disk. 
5% percent is for root usage and is reserved.
looking on this forum i found that there is a tool to kill the reserved space:

```
tune2fs -m 0
```

but there is still the problem of my 4.8 GB that are taken before the disk   
was mounted ,just after formating.

> **Predius said:**
> Not only that, but many HDDs are actually overrepresented, the buyed being told that the disk is bigger than it actually is.

if you read carefully my post you will see that i'm aware of that.

> **Quintin Riis said:**
> This doesn't really seem too out of the ordinary.  Any modern filesystem is going to have a bit of overhead.

then NTFS rocks since there is no overhead.
 no mater how you take it 20gb is A LOT of "overhead".

---

### Post by Quintin Riis on 2006-10-18
> then NTFS rocks since there is no overhead.
Totally incorrect.  No filesystem is going to give you 100% of the disk.  There exist MFT, journals, blah, blah, etc.

---

### Post by zekopeko on 2006-10-18
disk managment in winxp shows 0% overhead. perhaps there is a diffrence in what you think overhead is and what M$ thinks.

but the thing is that my 298.09 GB (this is formated capacity in winxp) has
298.07 GB free space under windows. around 150-200 MB are in use with the NTFS

---

