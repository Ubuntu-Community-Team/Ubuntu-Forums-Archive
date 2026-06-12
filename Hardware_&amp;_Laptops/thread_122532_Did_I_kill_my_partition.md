---
title: "Did I kill my partition?"
date: 2006-01-27
forum: Hardware &amp; Laptops
---

### Post by Nameless on 2006-01-27
Hello, 

I recently resized my /home partition using PartionMagic, but I think I may have caused a somewhat serious problem. 

When booting Ubunut, I now get a message at the "checking all file systems..." prompt.  It says "fsck failed...repair manually". 

So, I tried entering "fsck /dev/hda5" (which is where my /home directory resides) and I get the following message: 
> 
e2fsck: bad magic number in super-block while trying to open /dev/hda5

/dev/hda5:
The superblock could not be read or does not describe a correct ext2 file system.  If the device is valid and it really contains an ext2 file sytem, then the superblock is corrupt, and you might want to try running e2fsck wan an alternate superblock: 
e2fsck -b 8193 <device>


I'm not sure what I can do here.  Is there anyway to get my /dev/hda5 to be recognized again?

---

### Post by ]Nbx*cmD[ on 2006-01-28
Oops i'm afraid that was one of these "good jobs" done by partition magic :(
Last year i lost all my documents by resizing a partition too :(

---

