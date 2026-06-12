---
title: "Floppy Drive permissions problem"
date: 2005-05-03
forum: Hardware &amp; Laptops
---

### Post by granite230 on 2005-05-03
**edit:** This problem has been solved, but I'm not sure how I did it... I just tried and tried with some help of a friend and now it seems to work. 

First my floppydrive wouldn't work, I got this message:
*mount: I could not determine the filesystem type, and none was specified*

So it seems this fixed my first problem:
*granite@granite:~ $ sudo mount -t vfat /dev/fd0 /media/floppy*

Then I saw the floppydrive Icon on my desktop, but when I double-clicked it and draged a testfile in the floppy-window I got this message:

**Error while copying to "/media/floppy0".**
*You do not have permissions to write to this folder.*

Then I changed the permissions like this:
*root@granite:/media # chmod 777 /media/floppy0*

And now when I say: 
*root@granite:/media # ls -l*

I get this:
[I]lrwxrwxrwx    1 root     root            7 2005-01-25 10:39 floppy -> floppy0
drwxr--r--    2 root     root         7168 2005-05-03 14:10 floppy0[/I]

No permissions changed! So I can't write anything to a floppy disk since I don't have the write permission as a user!

How can I fix this second problem?

---

