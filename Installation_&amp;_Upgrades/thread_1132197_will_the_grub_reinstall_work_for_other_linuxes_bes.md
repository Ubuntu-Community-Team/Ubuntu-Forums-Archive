---
title: "will the grub reinstall work for other linuxes besides Ubuntu?"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by tamas305 on 2009-04-21
I was thinking about installing Arch or Faun OS onto a USB drive like I did with Ubuntu. I would need to relocate all of grub's files so that I will not get an error when the drive is not plug in. I used this code to relocate the files.

Into the terminal (in Ubuntu) I typed:

```
sudo grub
find /boot/grub/stage1
root (hd?,?)
setup (hd?)
quit
```

*I replaced the ? with the directory of the USB drive

Would this same method work if I typed this code into a Terminal in Arch for example?

Thanks in advance
-tamas

---

### Post by lemming465 on 2009-04-23
It should, yes.

---

