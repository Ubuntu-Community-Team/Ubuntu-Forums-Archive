---
title: "Mounting Windows Partition"
date: 2007-07-10
forum: Hardware &amp; Laptops
---

### Post by Dyegov on 2007-07-10
Sorry for all the questions. I promise this will be the last one, since after I fix the ones I posted, Ubuntu will be completely perfect :)

I dual boot with Windows XP, and still access a lot my info in that partition from Linux. When I want to mount the image I just have to go to Places -> Computer, double click it, input my password, and it's mounted. However, I have to do that every time I turn on the computer. Isn't there a way to make it stay mounted forever?

---

### Post by CheShA on 2007-07-10
you need to put an entry in /etc/fstab to mount the volume at boot.

---

### Post by Dyegov on 2007-07-10
> **CheShA said:**
> you need to put an entry in /etc/fstab to mount the volume at boot.

Would you mind to elaborate? I'm a Linux newbie, so I don't know how to do what you say :(

---

### Post by coffeecat on 2007-07-10
[Here's a good start]("http://www.tuxfiles.org/linuxhelp/fstab.html").

You need to backup /etc/fstab first (just in case). In a terminal:

```
sudo cp /etc/fstab /etc/fstab.backup
```And then edit it:

```
gksudo gedit /etc/fstab
```But before you do this, you need to know which partition Windows is on and you need to make a mountpoint for it. Post back with some more details and someone should be able to help you.

**Edit:** Oh, and don't apologise for all the questions. They're the lifeblood of the forum. :wink: Don't forget that for every person posting a question there will be a dozen silently searching the forums for the same issue and benefiting from the replies.

---

### Post by espo111 on 2007-07-10
install **ntfs-config**, use the package manager

here is its site:

[http://flomertens.free.fr/ntfs-config/](http://flomertens.free.fr/ntfs-config/)

---

### Post by Dyegov on 2007-07-10
> **espo111 said:**
> install **ntfs-config**, use the package manager

here is its site:

[http://flomertens.free.fr/ntfs-config/](http://flomertens.free.fr/ntfs-config/)

It solved the problem as easy as I could not have imagined, and it even gave me write access to the partition, which I was not expecting, but desired controllably. Thanks a bunch!!!

---

