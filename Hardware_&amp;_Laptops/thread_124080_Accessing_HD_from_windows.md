---
title: "Accessing HD from windows"
date: 2006-01-31
forum: Hardware &amp; Laptops
---

### Post by untree on 2006-01-31
I recently bought an external enclosure so I could access all the files on my old desktop HDs from my laptop (which is running XP).  One of those HDs, the one with the majority of the files I really want access to, was formatted for Hoary Hedgehog.  What windows software could I use to access this HD?  I tried LTOOLS, but it says the drive "is not ready" so I think perhaps it doesn't understand the formatting.

I never successfully got my CDRW drive to work under Hoary, so I couldn't just back the files up.  

Thanks in advance.

---

### Post by joft on 2006-01-31
Hi,

what do you mean by > formatted for Hoary Hedgehog?

If it's formated with ext2 or ext3 you could try

[http://ext2fsd.sourceforge.net/](http://ext2fsd.sourceforge.net/)

---

### Post by mips on 2006-01-31
[http://www.fs-driver.org/](http://www.fs-driver.org/)
[http://e2fsprogs.sourceforge.net/ext2.html](http://e2fsprogs.sourceforge.net/ext2.html)

Just check if you are using ext2 or ext3 file system on that drive. reserfs is not supported.

---

### Post by untree on 2006-02-07
Thanks for the tips, but I really have no idea what the filesystem is.  I just let Hoary format the harddrive however it wanted.  How can I find out what the filesystem is if I can't access the drive?  I can't boot up ubuntu now, since the computer is dismantled and the harddrive is converted to an external drive.

---

### Post by untree on 2006-02-07
I have tried to use ext2fsd but it says the hd isn't formatted.  I'm beginning to think maybe I should really just reformat the whole drive and say goodbye to my files.

---

### Post by mips on 2006-02-07
NO, wait dont format anything.

Boot off a LiveCD (Knoppix is better than the Ubuntu one but you can try the ubuntu one).
Try and mount the external drive or Knoppix might even mount it for you.
This will allow you to identify the filesystem.
Copy the stuff from your external HD to the internal one. 
Knoppix CD support might even work as it is one of the best livecds out there.

---

### Post by untree on 2006-02-07
Okay, thanks, I'll give that a try tonight when I get home from work, see if it works out.

---

