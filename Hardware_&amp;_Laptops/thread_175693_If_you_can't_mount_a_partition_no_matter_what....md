---
title: "If you can't mount a partition no matter what..."
date: 2006-05-13
forum: Hardware &amp; Laptops
---

### Post by transient on 2006-05-13
If you're trying to mount a partition and keep receiving the error: 
```
mount: /dev/hdxx already mounted or /dir busy
```
even though nothing seems to be wrong, try

/dev/evms/hdxx 

instead of

/dev/hdxx




Now the long story:

I have a second hdd connected as slave, which contains my windows installation. When i tried to mount the NTFS partition in that drive (dev/hdb1 in my case) , i received the error:
```
mount: /dev/hdb1 already mounted or /windows busy
```
However i was *sure* that 
- hdb1 wasn't already mounted
- /windows dir wasn't busy

So after a bit of googling, i saw this:
[http://lists.debian.org/debian-user/2004/11/msg01447.html](http://lists.debian.org/debian-user/2004/11/msg01447.html)

And there really was an "evms" (which stands for "Enterprise Volume Management System") folder under /dev , which also contained the device hdb1. And everything worked fine when i used /dev/evms/hdb1 when mounting :KS 

I just wanted to have this piece of information archived here in Ubuntu forums, in case it might be helpful to someone else.

...
emre

---

### Post by Waklevören on 2006-08-30
Wow, thanks mate! I would never have figured that out by myself! :D

I was really going crazy over this matter and was just about to give up before I decided to have a final, desperate, six-bullets-in-my-chest-go. And you really made my day now :D

Thanks a lot, mate.

I'm currently running Kubuntu Dapper, so this seems to be something that occurs throughout the different versions, although I just don't understand why.. And why it's never mentioned in any howto :s it really should be.

---

### Post by transient on 2006-08-30
Glad to hear it worked for you :D

I'm not sure why it happens either. I didn't have that problem before compiling my own kernel (2.6.16 vanilla kernel with the CK9 patch), so it probably has something to do with it.

.
e

---

### Post by bobcam on 2006-09-01
Waow

Thanks a lot for this solution !
I had the same problem since 2 days and nothing found or the net !!

I also don't know but it seems that it has something to do with kernel. I installed Xen 3. The mounting works well with "normal" Dapper kernel and this problem occures with Xen Kernel.

Thanks a lot for your help !

---

### Post by petrockthief on 2006-09-01
Nevermind, wasn't thinking, how do I copy terminal output to a text file?

---

