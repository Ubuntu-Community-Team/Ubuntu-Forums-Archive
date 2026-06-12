---
title: "mp3 player problem"
date: 2006-02-03
forum: Hardware &amp; Laptops
---

### Post by tanman on 2006-02-03
I am fairly new to linux and was wondering how to get Ubuntu to recognize my mp3 player.
When I plug it in it asks if I want to tranfer my pictures:( 
obviusly no pictures to transfer.;) 
If I look hard enough in the device section, can not remember where for I am at work, I can see it as a usb device and it even has the name of the player, but I can not open it or anything.
Any ideas would be great. 
I keep having to reboot to windows just to transfer music or podcasts. I can burn mp3's as a adio cd either.:(

---

### Post by o_fortuna on 2006-02-03
[QUOTE=tanman]I am fairly new to linux and was wondering how to get Ubuntu to recognize my mp3 player.
When I plug it in it asks if I want to tranfer my pictures:( 
obviusly no pictures to transfer.;) 
If I look hard enough in the device section, can not remember where for I am at work, I can see it as a usb device and it even has the name of the player, but I can not open it or anything.
Any ideas would be great. 
I keep having to reboot to windows just to transfer music or podcasts. I can burn mp3's as a adio cd either.:([/QUOTE]
What kind of mp3 player is it? Almost all mp3 players can be mounted simply by plugging them in, and it will appear as an icon on the desktop. Also, right after you connect it, you could type this into the terminal (Applications-->Accessories-->Terminal):
```
dmesg | tail
```
This may contain some useful information as far as whether or not Ubuntu sees your device as an external drive.

---

### Post by tanman on 2006-02-03
It is a phillips player. I just bought it abought a month ago. No problem with windows.
Ubuntu does see it, just as a camera. No icon or anything shows up just a window that asks if I want to transfer the pictures.

---

### Post by christhemonkey on 2006-02-03
IF its a gogear Phillips device then this application might be useful:
[http://freshmeat.net/projects/pygogear/]("http://freshmeat.net/projects/pygogear/")

---

### Post by darkwing|duck on 2007-08-15
ok i tried the attached website and i am either to stupid to make it work or it just dosent work, here is my what i get when i run the terminal

darkwingduck@darkwingduck-desktop:~$ dmesg | tail
[ 1345.976000] usb 2-3: new low speed USB device using ohci_hcd and address 46
[ 1346.160000] usb 2-3: device descriptor read/64, error -62
[ 1346.448000] usb 2-3: device descriptor read/64, error -62
[ 1346.728000] usb 2-3: new low speed USB device using ohci_hcd and address 47
[ 1346.912000] usb 2-3: device descriptor read/64, error -62
[ 1347.200000] usb 2-3: device descriptor read/64, error -62
[ 1347.480000] usb 2-3: new low speed USB device using ohci_hcd and address 48
[ 1347.888000] usb 2-3: device not accepting address 48, error -62
[ 1348.064000] usb 2-3: new low speed USB device using ohci_hcd and address 49
[ 1348.472000] usb 2-3: device not accepting address 49, error -62

---

