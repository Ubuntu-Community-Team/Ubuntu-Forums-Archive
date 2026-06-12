---
title: "Is it possible to mount an external hard drive as a local disk"
date: 2008-12-15
forum: Hardware
---

### Post by noogs on 2008-12-15
Hi, I recently set up my computer with Apache and have some of my files on the internet. The only problem is I want to be able to access my external hard drive from the internet as well. I've done some searching and found that the reason it cant be on the internet is it's shown as a temporary device rather than a local disk. So basically my question is does anyone know how to change the settings to make it mount as a local disk rather than a temporary drive or device. If not does anyone know another way to make an external hard drive show on an Apache server. Thanks in advance.

---

### Post by taurus on 2008-12-15
You can add an entry in /etc/fstab to have it mount automatically upon boot if that external harddrive is plugged in during boot.  Then, it would behave just like another drive.

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by noogs on 2008-12-15
Thank you very much this solved my problem.

---

