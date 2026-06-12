---
title: "problems with the X server"
date: 2008-02-10
forum: Hardware &amp; Laptops
---

### Post by nevia09 on 2008-02-10
:(
originally, I had problems with the automatic file system check (fsck),
but I guess I worked that out, but now I'm having problems with
my x server
[screenshot]("http://i19.photobucket.com/albums/b162/Moonyz1509/DSC06575.jpg")

---

### Post by overdrank on 2008-02-10
> **nevia09 said:**
> :(
originally, I had problems with the automatic file system check (fsck),
but I guess I worked that out, but now I'm having problems with
my x server
[screenshot]("http://i19.photobucket.com/albums/b162/Moonyz1509/DSC06575.jpg")

HI and welcome, what is the model of the graphics card? and you can click ok until you reach the command prompt and login. Then use this command to reconfigure your xorg ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` the use the command ```
sudo reboot 
``` hopefully this will bring you to the desktop (GUI)

---

