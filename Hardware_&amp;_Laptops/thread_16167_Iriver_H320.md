---
title: "Iriver H320"
date: 2005-02-19
forum: Hardware &amp; Laptops
---

### Post by danip on 2005-02-19
I own an iriver h320 mp3 player.  In the past it would always mount when i plugged it in and I could send music to it no problem.  Now all of a sudden it mounts when I plug it in but when i try to send music to it I get an error that says it is a read only disk.  Anyone know what is going on?

---

### Post by danip on 2005-02-20
by the way the mp3 player is fat32

---

### Post by danip on 2005-02-22
bump

---

### Post by MetalMusicAddict on 2005-02-22
Weird man. I have a H340 (see screenshot) and I dont have that problem. You might wanna look at the permissions on the drive. Right-click on the drive>Properties>Permissions. Make sure your the owner and you have the read, write, execute permissions set like you want.

[[img]http://img74.exs.cx/img74/8547/screenshotsmall2dz.png[/img]](http://img124.exs.cx/img124/2140/screenshot1ku.png)
Click image for 2560x1024

---

### Post by danip on 2005-02-28
Tried to change that got an error

The permissions could not be changed
Couldnt change the permissions of "sda1"
Because it is on a read only disk

---

### Post by danip on 2005-03-02
bump

---

### Post by MetalMusicAddict on 2005-03-02
Try logging in as root and changing them.

---

### Post by danip on 2005-03-03
how do i enable the root account so that i can log into it.

---

### Post by flyfishin on 2005-03-05
You don't need to enable the root account.  Use sudo to get root access.  Type: 'sudo su -' and enter your account password when prompted.

---

