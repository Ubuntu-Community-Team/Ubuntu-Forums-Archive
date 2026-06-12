---
title: "I can not umount cdrom"
date: 2006-08-21
forum: Hardware &amp; Laptops
---

### Post by jis on 2006-08-21
If I run umount /media/cdrom I get
"umount: /media/cdrom: device is busy
umount: /media/cdrom: device is busy".

Yes, I get twise the same text. I do not think that any application is using cdrom. (I am using Xubuntu Dapper.)

---

### Post by exjinn on 2006-08-21
are you trying to unmount this via a terminal? if so are you sitting in the cdrom directory?

---

### Post by jis on 2006-08-21
Thanks for your the prompt reply. Yes, I was trying to cut the branch where I was sitting on in a terminal. I still wonder why the error message was displayed twice. It would be nice, if the umount could give me a hint which program is using the cdrom.

---

### Post by hw-tph on 2006-08-21
Use the lsof command to find out what processes are using something. It is very useful for this kind of stuff, and for checking up on security as well.


Håkan

---

### Post by jis on 2006-08-21
I checked the command, but it is hard for a newbie like me to figure out from the man page how to use that for searching programs that prevent me from umouting cdrom.

---

### Post by atomkarinca on 2006-08-22
you can use this: "umount -l /media/cdrom". worked for me.

---

### Post by jis on 2006-08-22
I can also umount that way, but the file system of the cdrom remains usable. Isn't this against the idea of umount?

---

### Post by tgsim on 2008-04-09
Just wanted to say thanks for the useful info, Thanks


> **hw-tph said:**
> Use the lsof command to find out what processes are using something. It is very useful for this kind of stuff, and for checking up on security as well.


Håkan

---

