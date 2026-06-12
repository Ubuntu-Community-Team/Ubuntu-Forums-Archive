---
title: "Cannot modify fstab"
date: 2009-01-12
forum: Installation &amp; Upgrades
---

### Post by Evil Ninja on 2009-01-12
So, I was following the instructions to partition my second hard drive found [here]("https://help.ubuntu.com/community/InstallingANewHardDrive#Determine%20Drive%20Information") and I can't access my fstab to add the lines to it. Need help help fixing that.

---

### Post by logos34 on 2009-01-12
gksu gedit /etc/fstab

or

gksudo gedit /etc/fstab

or

sudo nano /etc/fstab

---

### Post by damphoud on 2009-01-12
Do you get any errors when you try to run:

```
sudo gedit /etc/fstab
```

?

---

### Post by Evil Ninja on 2009-01-12
> **damphoud said:**
> Do you get any errors when you try to run:

```
sudo gedit /etc/fstab
```

?

It said the "gedit" command was not found.

Using that "sudo nano" command worked, but I'm curious now as to why "gedit" won't.

---

### Post by logos34 on 2009-01-12
what, are you using kubuntu?

---

### Post by Evil Ninja on 2009-01-12
> **logos34 said:**
> what, are you using kubuntu?

Xubuntu, like I have it tagged.

---

### Post by damphoud on 2009-01-12
gedit is not installed in xubuntu by default.
you can use sudo mousepad.

---

### Post by hivelocitydd on 2009-01-12
sudo nano /etc/fstab

hope this will work

---

### Post by Evil Ninja on 2009-01-12
> **damphoud said:**
> gedit is not installed in xubuntu by default.
you can use sudo mousepad.

I see. Thanks.

---

