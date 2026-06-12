---
title: "Sound help Realtek ALC861 startup command"
date: 2007-08-11
forum: Hardware &amp; Laptops
---

### Post by jtchupp on 2007-08-11
Hello, I finally got my sound working following a few of the guides on this forum, but every time  I reboot I have to run these commands in order for it to work again.

sudo /etc/init.d/alsasound stop 
then

sudo modprobe -r snd-hda-intel && sudo modprobe snd-hda-intel 



So My question is, How can I set it up to run these commands on boot?

---

### Post by jtchupp on 2007-08-12
Bump

---

