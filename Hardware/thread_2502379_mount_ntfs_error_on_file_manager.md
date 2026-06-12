---
title: "mount ntfs error on file manager"
date: 2024-11-12
forum: Hardware
---

### Post by bigjohntw on 2024-11-12
Hello all, i've questions about mount error. My os is ubuntu 24.04.1. I tried to mount a NTFS device on file manager, it shows error dialog. But it was successfully mounted on terminal with bash command. Is it a bug on file manager? Is there any solution for this?

[IMG]https://imgur.com/DOM1UiY.png[/IMG]

---

### Post by yancek on 2024-11-12
Did you mount from a terminal immediately after failing in the file manager?  What command (exactly) did you use to mount.  The link below discusses the problem and gives suggestions such as Disable the User Session Default with an explanation of how to do it on 24.04.

[https://askubuntu.com/questions/1512710/wrong-fs-type-bad-option-bad-superblock-just-installed-lubuntu-24-04](https://askubuntu.com/questions/1512710/wrong-fs-type-bad-option-bad-superblock-just-installed-lubuntu-24-04)

---

### Post by Morbius1 on 2024-11-13
From the bug report: [https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/2062972](https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/2062972)

> Comment 18 for bug 2062972
Morbius1 (morbius1) wrote on 2024-09-04: 			#18

Do what nmaxx above did and blacklist the ntfs3 driver from running:

```
echo 'blacklist ntfs3' | sudo tee /etc/modprobe.d/disable-ntfs3.conf
```

Then reboot the box.

That will force the file manager to use the ntfs-3g driver like it did in Ubuntu 22.04



---

### Post by bigjohntw on 2024-11-13
> **yancek said:**
> Did you mount from a terminal immediately after failing in the file manager?  What command (exactly) did you use to mount.  The link below discusses the problem and gives suggestions such as Disable the User Session Default with an explanation of how to do it on 24.04.

[https://askubuntu.com/questions/1512710/wrong-fs-type-bad-option-bad-superblock-just-installed-lubuntu-24-04](https://askubuntu.com/questions/1512710/wrong-fs-type-bad-option-bad-superblock-just-installed-lubuntu-24-04)

Yes, after failing. i tried to use mount/umount/fuser commands on terminal. Thanks for your information. :D
```
mount -t ntfs /dev/sdx8 /home/xxx123/mdev123
umount /home/xxx123/mdev123
fuser -i -k -m -v /home/xxx123/mdev123
```

> **Morbius1 said:**
> From the bug report: [https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/2062972](https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/2062972)

so it's a bug? Thank you very much. :o

---

