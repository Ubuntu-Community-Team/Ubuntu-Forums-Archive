---
title: "File system question"
date: 2011-05-11
forum: Hardware
---

### Post by ClientAlive on 2011-05-11
Is there a file system that will work with both linux and windows? I have a 250 gig external hard drive I would like to re-format. I run Ubuntu 10.04; but, since it is an external drive, and most people use windows, I think there will be a lot of occasions where I need to access it from a windows machine as well.

Thanks in advance for any suggestions.

---

### Post by Yellow Pasque on 2011-05-12
ntfs or even fat32. If it's ntfs, always make sure you shut down or remove the device safely. ntfs can be a pain (force mounting, possible data loss) if that's not done properly.

---

### Post by ClientAlive on 2011-05-12
> **Temüjin said:**
> ntfs or even fat32. If it's ntfs, always make sure you shut down or remove the device safely. ntfs can be a pain (force mounting, possible data loss) if that's not done properly.


So you're saying my Ubuntu Linux system which is formatted in ext4 can make full use of an ntfs formatted drive? (Read, write, copy files back and forth, watch videos and play music from, etc)?

---

### Post by Yellow Pasque on 2011-05-12
> **ClientAlive said:**
> So you're saying my Ubuntu Linux system which is formatted in ext4 can make full use of an ntfs formatted drive? (Read, write, copy files back and forth, watch videos and play music from, etc)?
Yes.

---

### Post by ClientAlive on 2011-05-13
> **Temüjin said:**
> Yes.


Wow! So why are all these people on the net fussing about this topic? These guys are going through all kinds of grief over this.

And what about this "data corruption" people talk about?

---

### Post by Lars Noodén on 2011-05-13
> **ClientAlive said:**
> 
And what about this "data corruption" people talk about?

Neither NTFS nor FAT are modern, robust file systems and it is easy compared to other systems for them to fail in ways that lose data, especially FAT.  If you keep regular backups then there is less to worry about.

Alternately, you might look into getting or building a cheap SMB/CIFS NAS.

(FAT will probably become a big problem for digital photos as the chips used in cameras start to age.)

---

### Post by ClientAlive on 2011-05-13
> **Lars Noodén said:**
> Neither NTFS nor FAT are modern, robust file systems and it is easy compared to other systems for them to fail in ways that lose data, especially FAT.  If you keep regular backups then there is less to worry about.

Alternately, you might look into getting or building a cheap SMB/CIFS NAS.

(FAT will probably become a big problem for digital photos as the chips used in cameras start to age.)


I see. I thought that what file corruption meant had to do with some interaction between two different file systems. Now I think (maybe) it has more to do with just the particular file system; and, I imagine, this is what people are dealing with when they have to defrag windows file systems. Does that sound right?

So, if that is right, and I format in ntfs or fat I'll be dealing with that issue - and probably defragging the disk all the time. Right?

Thanks for helping me understand.

:)

---

### Post by Lars Noodén on 2011-05-14
> **ClientAlive said:**
> So, if that is right, and I format in ntfs or fat I'll be dealing with that issue - and probably defragging the disk all the time. Right?

Yes.  So when you boot into the linux partition each day, backup to an external hardisk formatted for EXT3 or EXT4 or anything else modern.

---

### Post by ClientAlive on 2011-05-14
> **Lars Noodén said:**
> Yes.  So when you boot into the linux partition each day, backup to an external hardisk formatted for EXT3 or EXT4 or anything else modern.

 Well that would be kinda difficult right now since it is the largest disk I own (by a longshot). I get what your saying though. I'll have to figure something out I guess. A way to back it up/ somewhere to put that much data. Been thinking about getting another external. I can get a couple terabytes these days for about a hundred bucks.

Thanks for your help man.

Jake

:)

---

### Post by ClientAlive on 2011-05-17
Thanks for all your help guys. I ended up choosing ext3 and have successfully reformatted that drive now. I just didn't want to have to deal with those Windows file systems. I figure I can transfer whatever I need onto my other thumb drive and transport it that way when I need to.

Have a great week fellas.

:D

---

### Post by Lars Noodén on 2011-05-17
> **ClientAlive said:**
>  I figure I can transfer whatever I need onto my other thumb drive and transport it that way when I need to.

Otherwise known as good, old [sneakernet](http://www.catb.org/jargon/html/S/sneakernet.html).  ;)

---

### Post by ClientAlive on 2011-05-17
> **Lars Noodén said:**
> Otherwise known as good, old [sneakernet](http://www.catb.org/jargon/html/S/sneakernet.html).  ;)

 lol. Good one.

:D

---

