---
title: "USB drive doesn't delete space"
date: 2007-05-18
forum: Hardware &amp; Laptops
---

### Post by CaptainCommandLine on 2007-05-18
I'm using 7.04. I have a 4gb usb key. 

/dev/sdb1             3.9G  3.6G  302M  93% /media/disk

There is only 300mb available, but the disk is empty, all files have been deleted.

On windows, i see the full space available.

Does anybody have an idea or have a similar problem?

Thanks!

---

### Post by adastra23 on 2007-05-18
I had a similar problem, what you describe may not be the same thing. Being new to Linux, I didn't realize that there was a hidden directory called .trash on external drives when files are deleted from them. You say that windows sees the drive as empty. That is how I discovered the space problem, was plugging it into a windows machine and seeing the .trash folder - just like in my home directory in Ubuntu. 
hope that helps.
It was a head scratcher for me that night.

---

