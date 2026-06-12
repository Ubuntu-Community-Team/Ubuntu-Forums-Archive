---
title: "How to get Second HDD recognized"
date: 2005-02-14
forum: Hardware &amp; Laptops
---

### Post by ryharv on 2005-02-14
Hello,

I recently installed a second hard drive on my machine.  Now, running **df** on the command line gives me:

> Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1              7759252   1623412   5741692  23% /
tmpfs                   128468         0    128468   0% /dev/shm
/dev/hdb1            192292124     32828 182491376   1% /opt2

/dev/hdb1 is the second hard drive.  I have mounted it to **./opt2**.  

Back in the desktop, when I open the folder opt2, it says there are 175 free Gbytes.  However, the folder appears to be read-only.  All the other folders in the file system say (at the bottom of the window, when I open a folder in the file tree) say that there is 5.5 GB available on the hard drive (i.e., the space available on the first hard drive).

I can use **mkdir** to write a folder to /opt2 from the command line, but I cannot drag a file to opt2 from the desktop.  

Can someone please tell me how I can move files onto the drive from the Ubuntu desktop?

Many thanks.

---

### Post by ryharv on 2005-02-15
i figured it out -- i could write to it from the terminal because i was root, and by changing settings with chmod, i was able to make it accessible to me back on the desktop.

---

