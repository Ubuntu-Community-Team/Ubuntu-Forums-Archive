---
title: "HOw can I rename a drive that auto-mounts?"
date: 2005-06-10
forum: Hardware &amp; Laptops
---

### Post by jzke on 2005-06-10
Hey I have a USB drive that is great, and works perfectly with Ubuntu. My only complaint is the icon on the desktop and in the "Computer" as "131M Removable Drive"... which I think is useless. 

Is there anyway to change this label, so everytime it automounts it says something different?

---

### Post by Alexander Kirillov on 2005-06-11
[QUOTE=jzke]Hey I have a USB drive that is great, and works perfectly with Ubuntu. My only complaint is the icon on the desktop and in the "Computer" as "131M Removable Drive"... which I think is useless. 

Is there anyway to change this label, so everytime it automounts it says something different?[/QUOTE]
 It is supposed to show more meaningful names. 

Try running 
sudo /etc/init.d/dbus-1 restart
Does it help? 
If yes, you have come upon infamous [HAL/DBUS](http://ubuntuforums.org/showthread.php?t=27087) bug

---

### Post by jzke on 2005-06-30
Well, there you go it kinda worked. It now appears as "usbdisk"... but I was hoping to manually rename it... any chance of this happening?

---

### Post by Neovalis on 2005-12-14
I was wondering the same thing.  You can rename partitions in windows and it shows up that way in ubuntu.  How do you do it from ubuntu?  Is it possible to rename external ext3 partitions as well?

---

### Post by Neovalis on 2005-12-14
check out this thread ->
[http://www.ubuntuforums.org/showthread.php?t=24127&highlight=rename+drive+label]("http://www.ubuntuforums.org/showthread.php?t=24127&highlight=rename+drive+label")

---

