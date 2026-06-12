---
title: "VFAT File Permissions"
date: 2009-09-01
forum: Hardware
---

### Post by fuzzman54 on 2009-09-01
I have a VFAT hard drive mounted and I made a group will all of my systems users and added that you the fstab with umask 000, but it still isn't writeable. How do I fix it? I don't want certain permissions on certain files or folders, I just want the whole thing to have read, write, and execute permissions.

---

### Post by fuzzman54 on 2009-09-02
Okay,I found out how to make it writeable, but how do I make it so that all users can write to it?

Nevermind. I thought I found out how to make it writeable. I was wrong.

---

### Post by fuzzman54 on 2009-09-02
umask,fmask,and dmask have no effect. Even though I have them in fstab, when I mount the drive it always has the permissions set to 755.

---

### Post by fuzzman54 on 2009-09-03
?

---

### Post by Chronon on 2009-09-03
I believe that umask, etc. can only restrict privileges, not grant them.  Have you tried to chmod a+w to make the drive writable?  VFAT doesn't support most privileges, but apparently unsetting the writable attribute is equivalent to setting the read only flag in Windows.

---

### Post by fuzzman54 on 2009-09-03
Yep. Didn't do anything. Still has the file permissions of 755.

---

### Post by Chronon on 2009-09-03
So, the command executed without any error but didn't change anything?  What command did you issue, specifically?

Maybe the file system is broken somehow.  You could go for a fsck.vfat to see if it finds (and can fix) any problems. This was the resolution, at least in this case: [http://ubuntuforums.org/showthread.php?t=436335&page=2](http://ubuntuforums.org/showthread.php?t=436335&page=2)

---

### Post by fuzzman54 on 2009-09-03
I've used "sudo chmod 777 /media/SPARTAN" and "sudo chmod a+w /media/SPARTAN"

---

### Post by Chronon on 2009-09-03
Hmm... a damaged file system is the only thought I have currently, sorry.  If that doesn't work then maybe someone else will have an idea about this.

---

### Post by fuzzman54 on 2009-09-03
Thanks for the effort. :D

---

