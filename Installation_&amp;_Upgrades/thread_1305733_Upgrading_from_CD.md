---
title: "Upgrading from CD"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by C_Bomb on 2009-10-30
Hi,

I downloaded the new Ubuntu 9.10 ISO image and burnt it to a disc.
But, How can I use that cd to upgrade? When i run the installation it doesn't give me an upgrade option.the only option it gives is to install a clean version. And i don't have the luxury of the internet. So I can't upgrade like how the other guys do.

Any help?:)

---

### Post by mathfeel on 2009-10-30
On the Alternative CD, there is a command on the root has a script called cdromupgrade. So (as root, or use sudo):

```
$ mount -t iso9660 -o loop /path/to/alternative.iso /cdrom
$ sh /cdrom/cdromupgrade
```

---

### Post by C_Bomb on 2009-10-30
cool thanks, I'll give it a try when I'm back home.

---

### Post by C_Bomb on 2009-11-05
no that doesn't work.....Let me put this straight....i downloaded the new ubuntu 9.10 from their website....burnt the image to a cd.....

How can i upgrade from the cd without having ti format my hard drive.

---

