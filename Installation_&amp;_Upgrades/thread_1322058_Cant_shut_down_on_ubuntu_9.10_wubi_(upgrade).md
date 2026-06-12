---
title: "Cant shut down on ubuntu 9.10 wubi (upgrade)"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by yalgret on 2009-11-10
Sorry if this is posted already but I cant find any help.
I recently upgraded to ubuntu 9.10, it works ok (few little errors though)

However I cannot shutdown, it fails and I have to use the powerswitch.

I get this:

```
*Deactivating swap
[25769.984117]Buffer I/0 error on device loop0, logical block 3787587
```
Can anyone help me because it could be damaging my computer switching off and I already have some errors on my hardrive (says disk utility)


](*,):confused:

thanks

---

### Post by jhoms on 2009-11-11
Hi,

I fixed it following instructions from Agostino in post#19 for BUG#468589.
 
[https://bugs.launchpad.net/wubi/+bug/468589](https://bugs.launchpad.net/wubi/+bug/468589)

Hope it helps.

---

### Post by yalgret on 2009-11-11
Thanks ill try it

---

### Post by yalgret on 2009-11-11
I dint uderstand how to fix it and do not want to risk editing the grub ect.

But I heard that it will be fixed through an update so shall I just wait for the patch?

Thanks for answering though

---

### Post by jhoms on 2009-11-11
I guess it will be fixed sooner or later. If you can survive doing the powerswitch you could wait.
 
Regarding the changes posted in the bug, you're not editing GRUB but another file: /etc/rc6.d/S40umountfs.

I made a backup so I can revert it at any time. I chosen not to wait. ;)

---

### Post by yalgret on 2009-11-13
What can i do to fix it then?
And how long will it take to get fixed?

---

### Post by jhoms on 2009-11-13
In the [lasts posts]("https://bugs.launchpad.net/wubi/+bug/468589/comments/89") from BUG#468589 they're pointing to patches for 32 and 64 bits.

For 32 bit ubuntu:
[http://archive.ubuntu.com/ubuntu/pool/main/s/sysvinit/initscripts_2.87dsf-4ubuntu12_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/sysvinit/initscripts_2.87dsf-4ubuntu12_i386.deb)

For 64 bit ubuntu:
[http://archive.ubuntu.com/ubuntu/pool/main/s/sysvinit/initscripts_2.87dsf-4ubuntu12_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/sysvinit/initscripts_2.87dsf-4ubuntu12_amd64.deb)

You could try it to see if you're problem gets fixed.

---

