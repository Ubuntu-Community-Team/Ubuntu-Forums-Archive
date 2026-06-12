---
title: "crystal eye webcam in hardy. no dice."
date: 2008-08-17
forum: Hardware
---

### Post by uncannybuzzard on 2008-08-17
ok, i bought a new acer extensa 5420 and it has a crystal eye webcam built in. this is the one made by
suyin. anyway, after doing some research i find that this thing is supposed to be supported by the uvcvideo
driver. so, i've installed the newest build of that from svn. moved the old one etc, but still i cannot get
this thing working. i keep getting this in dmesg:

```
ian@JEEZI-CREEZI:~$ dmesg | grep uvcvideo
[   31.050789] uvcvideo: Found UVC 1.00 device Acer CrystalEye webcam (064e:a101)
[   31.157845] usbcore: registered new interface driver uvcvideo
[  322.049307] uvcvideo: Failed to query (135) UVC control 2 (unit 3) : -110 (exp. 2).
[  322.950457] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
```

anyone have any ideas?

i installed the new uvcvideo driver by altering the Makefile to change the path of the installation
directory as per a few threads i've seen on this, and symlinked it to the other directory for good measure.

---

### Post by uncannybuzzard on 2008-08-18
bump

---

### Post by nomind111 on 2008-10-30
hey, i got no idea how to get crystal eye installed on 5520-5156 acer. im reading forums on it...i am a confused noob. haha i need a beer...

---

