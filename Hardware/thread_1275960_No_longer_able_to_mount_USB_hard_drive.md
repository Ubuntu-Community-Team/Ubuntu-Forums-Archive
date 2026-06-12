---
title: "No longer able to mount USB hard drive"
date: 2009-09-26
forum: Hardware
---

### Post by Kreuger on 2009-09-26
Im using Xubuntu Karmic and after recently installing some updates, I'm no longer able to mount my usb hard drive. Thunar says

> Unable to mount "Storage":

No device with id /org/freedesktop/Hal/devices/volume_uuid_588fc740_d976_4134_9978_ac31e2222c50
However when I go into my /media folder Storage now reads as Storage_ so I tried changing deluge to reflect this and it's still unable to read any data from it. However I can read all the files through Thunar if I go to /media/Storage_ so I guess it changed the name of the folder and that killed my symlink? Im not sure what's causing Deluge problems though.

---

### Post by dagoth_pie on 2009-09-26
Deluge is set up to use the
```
/media/Storage_
```
folder correct?

If you're sure you have that right, I can only suggest maybe you have some problem with your permissions, stopping Deluge from being able to read/write to the hard drive.

Ideas anyone?

---

### Post by Kreuger on 2009-09-26
Yeah that's right. But my files say they're "checking" which Ive seen before when it wasnt able to mount the drive. I never changed the permissions but after looking at them just now, they appear fine. I have full read/write access.

---

