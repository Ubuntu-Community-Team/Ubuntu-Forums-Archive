---
title: "Seagate FreeAgent External HDD Readonly"
date: 2008-01-05
forum: Hardware &amp; Laptops
---

### Post by explosive on 2008-01-05
Hi,

I have been trying to mount my external HDD so that I can write to it. I have formated it as ext3 but it still mounts read-only!

I have applied the script described here: [http://ubuntuforums.org/showthread.php?t=494673](http://ubuntuforums.org/showthread.php?t=494673) but that had not fixed the problem.

Any ideas?

---

### Post by deadofied on 2008-01-05
I have the same problem- my 320 GB Seagate FreeAgent mounts as Read Only. I haven't formatted it as ext3 though. Help would be greatly appreciated!

---

### Post by Daelyn on 2008-01-05
Just a stupid thought, but, is it possible it is user rights that cause your issue?

If you do 
```
 sudo chmod 777 /your mount point 
```
you will change the access rights to the "folder".

As base, ubuntu will only allow "user" to mess about in the own "/home/###" folder and nowhere else. but, using the chmod 777 will change access rights to the location you point at to be "free for all".

This will only apply to linux filesystems (and other "user rights" based??), but, as you've stated it is ext3 formatted which makes it a part of the "maybe" problem.

---

### Post by explosive on 2008-01-06
Changing chmod hasn't made any difference.

I've been playing a bit and the only way I can get write access is to launch nautilus as root from the command line! - which is obviously not an ideal solution...

---

### Post by vanadium on 2008-01-06
As root, create a directory on that drive, and change the owner of that directory to yourself as user. Then you will have full rights as a user in that directory.

---

### Post by explosive on 2008-01-06
That seems to be doing the trick! Thanks :)

---

