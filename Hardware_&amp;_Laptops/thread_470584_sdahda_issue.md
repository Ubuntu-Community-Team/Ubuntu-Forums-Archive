---
title: "sda/hda issue"
date: 2007-06-11
forum: Hardware &amp; Laptops
---

### Post by amitst on 2007-06-11
Hi,

I have mounted two NTFS drives in Ubuntu Feisty Fawn on my laptop. I have following entries in my /etc/fstab,

/dev/sda1    /media/windowsc ntfs  nls=utf8,umask=0222 0    0
/dev/sda5    /media/windowse ntfs  nls=utf8,umask=0222 0    0

However, sometimes I have observed that the NTFS partitions fail to mount. The reason being the files /dev/sda1 and /dev/sda5 disappear and /dev/hda1, /dev/hda5 appear instead. What may be  causing this?

Amit

---

### Post by pestilence on 2007-06-11
I noticed the same with my Kubuntu installation, only to realize that my HD letters changed after installing ntfs-3g and ntfs-config.

---

