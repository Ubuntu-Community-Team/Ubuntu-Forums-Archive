---
title: "Boot problem"
date: 2008-08-27
forum: Hardware
---

### Post by pumber on 2008-08-27
Hi

I have problem in booting Ubuntu.

When it boots, it displayed 

[COLOR="Blue"]waiting for root file system[/COLOR]

and then after a few mins, stops at a prompt.

Actually, I remove one of the  two harddisks  and then this problem arises.

What can I do ?

I am a newbie in Ubuntu, I would be much appreciated if your reply is in detail .

Thank you !

---

### Post by silvanus2005 on 2008-08-27
Reinstall Ubuntu on your system, it should solve your problem.

---

### Post by hessiess on 2008-08-27
> Actually, I remove one of the two harddisks and then this problem arises.

something referanced in /etc/fstab is on the disk you took out i.e. /home. hence it wont boot.
can you post
```
sudo nano /etc/fstab
```

---

### Post by pumber on 2008-08-27
It shows

[COLOR="DeepSkyBlue"]
/bin/sh:sudo : not found[/COLOR]


What can I do now ?

---

