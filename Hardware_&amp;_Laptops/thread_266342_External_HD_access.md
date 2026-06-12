---
title: "External HD access"
date: 2006-09-27
forum: Hardware &amp; Laptops
---

### Post by hiena on 2006-09-27
My external HD (NTFS) doesn't show in the Desktop but shows in Nautilus, but when try to browse it says just 'root' can mount it, even though am using the 'root' userid.
Tried to mount it using the command line and ok. Shows in Desktop 
but still says I don't have permission to it.

Using Admin/Discs. I disable and then enable and then at least I can read but then no write...
Any quick fix to it? I know there is a problem to read/write to NTFS and would be glad to format it for Linux but then all my music, about 100GB, is in there...

---

### Post by kazuya on 2006-09-27
you can look up ntfs-progs, etc. I believe you may have to install this to get write access to an NTFS partition. Be sure to check the stability of it though as I have read somewhere that you need to upgrade it in a special manner or so. Look up Search under Ubuntu forums for topic on how to install it and how to use it..

I hope this helps.

Some used to use Captive-ntfs, but NTFS-progs is most acceptable here.

To be safe, I'd just copy all those datas to a partition somewhere and reformat as FAT32, for ease of working with the external device.

---

### Post by hiena on 2006-09-27
I think I will go for the fat32 advice...
I am getting sick of all this ntfs this and that that never work anyway. I must have tried a few by now including 'ntfs-3g' and 'ntfs-progs' and there is always something that goes wrong before you get to the end of the how-to...
Thanks a lot!

---

### Post by hiena on 2006-09-27
Ok it's done!
I used the forum entry below...and it worked!
[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by kazuya on 2006-09-29
cool. good choice. Best of luck.

---

