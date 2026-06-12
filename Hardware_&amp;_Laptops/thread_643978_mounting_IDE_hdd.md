---
title: "mounting IDE hdd"
date: 2007-12-18
forum: Hardware &amp; Laptops
---

### Post by dawp on 2007-12-18
i have an ide disk that i do not want to format and mount to location /home/music. I had this disk on another distro (opensuse) and would not like to lose the data. when i installed unbuntu and specified the sata drive, the system would put the boot loader on the ide as default so i unplugged,installed and replugged. system sees it, mounted at first but after I manually unmounted it, the system refuses to mount it, as it sees it labled as /home/music/ and refuses to mount it or allow me to rename it. the only option gparted gives me is to format it and i do not want to do that yet, atleast until i can mount it and copy the contents to my sata drive.


oh, by the way this a ext3 format on the drive.

---

### Post by taurus on 2007-12-18
Is it /dev/hda1 or /dev/sda1?
```
sudo fdisk -l
```

Have you tried to add an entry in /etc/fstab to mount it every time you boot Ubuntu?

You can change the ownership of /home/music from root to your login name so you can write to it anytime you want.

---

### Post by dawp on 2007-12-18
i'm having trouble changing permissions, what is the easiest way to do that?

It's /dev/hdc1

---

### Post by dawp on 2007-12-19
anyone?

---

### Post by dawp on 2007-12-20
?

---

### Post by logos34 on 2007-12-20
> **dawp said:**
> i'm having trouble changing permissions, what is the easiest way to do that?

It's /dev/hdc1

this should help:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by dawp on 2007-12-27
When I try to mount the drive manually it tells me that the mount point does not exist.

How do I go about creating a mount point?

---

### Post by taurus on 2007-12-27
```
sudo mkdir /media/*your_mount_point*
```

---

