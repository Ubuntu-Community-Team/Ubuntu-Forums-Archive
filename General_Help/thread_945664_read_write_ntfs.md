---
title: "read write ntfs?"
date: 2008-10-12
forum: General Help
---

### Post by AGSzabo on 2008-10-12
hellau,

s ubuntu now able to safely read and write ntfs partitions?

thats all for now,
greets,
AGS

---

### Post by earthpigg on 2008-10-12
yup

---

### Post by AGSzabo on 2008-10-12
wow. taht was fast. thank you!

but then, why can it be good to convert to annother format?

---

### Post by bodhi.zazen on 2008-10-12
If you do not run Windows you will not be able to debug the file system.

---

### Post by AGSzabo on 2008-10-12
i guess its a matter of time until its possible to debug ntfs from linux.

so btw, does ntfs support user/group/other rigths managment? is that fully compatible to linux seen from the linux-side? i.e. can i make my home-dir ntfs and get the rights set as if it was a linux native partition?

thank you again

---

### Post by bodhi.zazen on 2008-10-12
> **AGSzabo said:**
> i guess its a matter of time until its possible to debug ntfs from linux.

Possibly ...

> so btw, does ntfs support user/group/other rigths managment? is that fully compatible to linux seen from the linux-side? i.e. can i make my home-dir ntfs and get the rights set as if it was a linux native partition?No, not at all. You set ownership and permissions at the time of mounting and these same ownership and permissions are set to every directory and file on the ntfs drive.

You can have some *limited* control with umask, dmask,and fmask

I suggest you look at man mount

[http://linux.die.net/man/8/mount](http://linux.die.net/man/8/mount)

In addition you can not use a NTFS partition for /home or install linux onto it (due to the lack of permissions).

IMO, if you are running Windows and need a shared partition, NTFS is a good choice. Take care to scan it from time to time for viruses (from windows).

If, however, you are not running or sharing with Windows, I suggest you convert to a linux native file system.

> thank you again

You are most welcome. You can find a lot of information here :

[http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

---

### Post by AGSzabo on 2008-10-12
ok, now i know. thank you

i think i should make a home partition with ext3 and a shared data partition with ntfs.

with this config i can reinstall any linux while home stays as is.

---

### Post by AGSzabo on 2008-10-12
btw, your suggested page about ntfs reads that ntfs CAN handle user rights. what is the truth:

> POSIX file system operations are supported, and full file ownership and permission support is available as well

---

### Post by bodhi.zazen on 2008-10-12
I just saw that as well.

I read the page and it seems it is in Beta.

So I would say they are working on it, but I would not use it on a "production" machine.

---

### Post by AGSzabo on 2008-10-12
ok

---

