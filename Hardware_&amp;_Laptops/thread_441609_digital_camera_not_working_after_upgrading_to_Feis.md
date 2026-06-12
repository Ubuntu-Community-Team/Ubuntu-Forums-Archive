---
title: "digital camera not working after upgrading to Feisty"
date: 2007-05-12
forum: Hardware &amp; Laptops
---

### Post by laytek on 2007-05-12
Please forgive my frustration, but now that I have upgraded to Feisty, I can longer plug in my Canon Powershot A540 and move my pictures. It has been working fine (Dapper).  Please help!](*,)

---

### Post by vikram on 2007-05-13
to help in debugging your problem post the output of the following commands after plugging in your camera

lsusb

dmesg

tail -n 20 /var/log/messages

---

### Post by laytek on 2007-05-17
Vikram,

I must learn to take my time when encountering problems. 

The solution is already documented. It seems that upgrading from Dapper to Edgy (and Feisty) cause some type of problem with GNOME. Simply delete ~/.gconf/desktop/gnome/volume_manager for each user that has the problem. See [http://ubuntuforums.org/showthread.php?t=418242](http://ubuntuforums.org/showthread.php?t=418242) As soon as I did this, the camera was detected and everything worked normally.

Thanks for your time responding to this thread.

LayTek

---

