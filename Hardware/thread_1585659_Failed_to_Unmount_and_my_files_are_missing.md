---
title: "Failed to Unmount and my files are missing"
date: 2010-09-30
forum: Hardware
---

### Post by jacobroecker on 2010-09-30
Ok all:

I did the "unpardonable" I pulled a USB drive without "unmounting" it and it's got 700GB of information I want to be able to retrieve.  I can see the "recycled" folder when I plug it in now, but not the folder with the files. 

The information is still taking up space because the drive still lists the same amount of used space / free space as before.  The files are very very important.

I am currently running 8.04 (my favorite ;-) and have at my disposal a mac running OS X in case the solution requires a second machine.

Please help!

What else do I need to tell you in order for you to help me?

---

### Post by Dark_Stang on 2010-09-30
What filesystem was on the drive? Please don't say Fat32.

---

### Post by jacobroecker on 2010-10-01
I won't "say" it, but I will confirm it by typing...

---

### Post by IcarusR on 2010-10-01
You have two choices, either plug into windows box & run chkdsk or run fsck.vfat (see man page) from ubuntu. Don't know if you can check fat32 from Mac OS, suggest you google that.

First is preferable in my opinion.

I would recommend taking an image of the drive first, in case it gets fubared, thus maximising chances of not loosing any data.

---

### Post by jacobroecker on 2010-10-02
It was easier than I thought to get it working.  As it turns out the MAC's "Disk Utility" has features designd to deal with just this problem.   All I had to do was hook it up to the MAC and tell it to "repair"  G2G.

Thanks guys.  Without your input I would have thought it was impossible.

-Jacob

---

### Post by Dark_Stang on 2010-10-02
Now do yourself a huge favor, and get a journaled file system on that drive. Just remember to back up your stuff before reformatting or you're going to be really angry.

---

### Post by jacobroecker on 2010-10-02
I need to afford another drive with 700GB worth of space before I can do anything, but your point is certainly well taken.

Thank you!

---

