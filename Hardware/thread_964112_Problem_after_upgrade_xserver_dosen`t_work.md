---
title: "Problem after upgrade xserver dosen`t work"
date: 2008-10-30
forum: Hardware
---

### Post by bazu on 2008-10-30
[[img]http://i.data.bg/08/10/31/1221960.jpg[/img]](http://i.data.bg/08/10/31/1221960_orig.jpg)
after this i try 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and try with vesa drivers
[[img]http://i.data.bg/08/10/31/1221964_t.jpg[/img]](http://img.data.bg/i.php?id=1221964)
And this is my xorg.cong 
[[img]http://i.data.bg/08/10/31/1222002_t.jpg[/img]](http://img.data.bg/i.php?id=1222002)

---

### Post by lifelesspoet on 2008-10-31
I had that exact problem.  First when i used the beta 8.10, Just after installing nvidia-glx-177 and then upgrading from 8.04 which had the nvidia drivers installed already.  I'm suspecting your install is having a problem with drivers.  I have read on forums that there are problems with nvidia drivers and the new kernel.  The alternative is to either rollback the upgrade or use the open source 2d video card driver.

---

### Post by bazu on 2008-10-31
> **lifelesspoet said:**
> I had that exact problem.  First when i used the beta 8.10, Just after installing nvidia-glx-177 and then upgrading from 8.04 which had the nvidia drivers installed already.  I'm suspecting your install is having a problem with drivers.  I have read on forums that there are problems with nvidia drivers and the new kernel.  The alternative is to either rollback the upgrade or use the open source 2d video card driver.Ok but my video card is Ati radeon and I already know where is the problem but i can`t fix it. When i start original xorg.conf i and i have problem with "screen" only. If someone can tell me plece.

---

