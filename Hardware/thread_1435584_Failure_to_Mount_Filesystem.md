---
title: "Failure to Mount Filesystem"
date: 2010-03-21
forum: Hardware
---

### Post by haidaguy on 2010-03-21
So, I booted up my computer a few days ago and what came up was an error message saying "Failure to mount filesystem". Now when I try to boot up from the HDD the word GRUB comes up over the entire screen and the bottom right keeps flashing as if it is writing GRUB over and over again. My father thinks the loader might be broken but we cannot figure out how to fix this problem. 
Help?
Karmic Koala 9.10
Dell Inspiron 1521

---

### Post by krfulton on 2010-03-25
I have seen this too, I got it on my desktop system with 9.10 and a new sata hd, after reboot, i got the flashing GRUB.

Anyone else ever see this? or know how to fix, if my computer won't mount or boot to the HD?

---

### Post by Quikestore on 2010-04-26
I had this happen to me today.  What seems to have happened is there was a failure to mount the main file system, so what I did was run fdsk at root to look for and repair any errors they may be to the Ubuntu partition.  If the main file system failed to mount it should be safe to run at root.  Once this is done take a look at what errors you are getting and make the proper decisions on that info.  In my case, for some reason there were missing or corrupted values for my inodes so I guess when file mounting begins, the system looks for these hard links on the system and uses those as pointers for the file system.  I am still a newbie, but I think that is the issue.  But nonetheless, I ran fdsk when the main file system failed to load and it helped me solve my issue.

Hope this helps someone out! :P

---

