---
title: "usb floppy"
date: 2011-03-24
forum: Hardware
---

### Post by macstl on 2011-03-24
Got 10.10 on a t23 thinkpad. I plug in usb floppy drive and it shows on places and "computer" It goes through the motions of a format all ok. But it won't open to see whats on the floppy. says no media and won't mount. What am i doing wrong?

---

### Post by macstl on 2011-03-26
I found the problem listed on a thread after mine and am trying to use the fix.
I type "udisks --mount  /dev/sdb and the drive makes a seek with disk in.
If I have a linux formated disk in;it says I must tell the file type .
10.10 is using ext4 but I can't figure out the syntax to add it on to the above command.

If i run the above command with out floppy disk inserted it says it don' t recognise the device. 
 please help
thanks

---

### Post by macstl on 2011-03-26
I put a freshly dos formated diskette in and it works with the "fix" line of code I mentioned earlier.
However , If i goto the disk utility and format it with linux as mbr the fix line of code does not recongnize the file format and the floppy icon on desktop goes away. So I guess I can say its half fixed.
I justed wanted to b/u by firefox bookmarks , so Dos disk serves that purpose.:D

---

