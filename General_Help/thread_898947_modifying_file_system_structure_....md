---
title: "modifying file system structure ..."
date: 2008-08-23
forum: General Help
---

### Post by pmooney78 on 2008-08-23
I've got an old IDE hard drive that I'd like to mount as /tmp. I dropped it into an open IDE port, formatted as ext2, checked for errors, and modified /etc/fstab so I can mount it (currently as /media/Extra). Everything works fine, but I'm leery about trying to just modify fstab so that it mounts as /tmp. Do I worry about permissions? Ownership? And there's already stuff in my /tmp folder! Do I have to remove it? In general, can I move system directories that were automatically created during install (/usr, /bin, etc) to an external drive? How would I do so?

I'm running Xubuntu 8.04 on a Pentium III 550 MHz, and would be happy to provide more about my system configuration if it's helpful. :)

---

### Post by Patb on 2008-08-23
> **pmooney78 said:**
> Everything works fine, but I'm leery about trying to just modify fstab so that it mounts as /tmp. Do I worry about permissions? Ownership?  You might have a look at [this howto on fstab]("http://ubuntuforums.org/showthread.php?t=283131").

> And there's already stuff in my /tmp folder! Do I have to remove it?
Generally it is better to mount a partition on a directory which is empty.  Helps to prevent confusion as to just where the data is. Apart from that, why use /tmp? That directory is commonly used by programs. Perhaps /home/tmp would be better? 

And I wouldn't try to move "system directories". 

Hope this helps. Cheers, Pat.

---

### Post by pmooney78 on 2008-08-30
Thanks. I really did want to mount it as /tmp to use it as temporary program storage (because I have an old Frankenstein system spanning several small hard drives, I need one to provide enough temporary storage space to allow burning DVDs :). Eventually solved the problem by re-installing the OS, specifying /dev/sdb1 mount as /tmp in the install options. Much simpler that way, and I can leave packages updating while I walk to work.

That fstab tutorial is great. Thank you for your help.

---

