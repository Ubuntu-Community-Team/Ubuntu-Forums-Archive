---
title: "Help installing Ubuntu/Kubuntu"
date: 2009-03-03
forum: Installation &amp; Upgrades
---

### Post by neer2005 on 2009-03-03
Hi I have burned a kubuntu iso onto a cd and i boot from cd but then after the loading screen it gives me this command line [IMG]http://i43.tinypic.com/hsjsd3.jpg[/IMG] I also tried downloading Ubuntu also but i still get the same screen Please I am sort of new to linux and I really need some help thanks in advance

---

### Post by whoop on 2009-03-03
It is some kind of I/O error. Check the cd for defects using the option when you boot from cd. If there is nothing wrong with the cd then it could be your drive. If you are running windows on that drive do a full disk check.

---

### Post by neer2005 on 2009-03-03
I have made like 4 copys all different downloads with poweriso and my hard disk is partitioned im installing it on a whole other partition than windows

---

### Post by avtolle on 2009-03-03
The error messages all refer to device sr0, which is your CDRW drive (IIRC), indicating to me that there is either a problem with that drive itself, or more likely with the CD in the drive. Before you burned the iso to the CD(s), did you check the md5sum of the iso to see if it may have been corrupted during the d/l process? When burning as an image to CD, it is my suggestion that the burn be done at a low speed; for me, 4x always works; 8x works almost always. And, as suggested previously, check the CD for defects at the initial menu of the Live (Desktop)CD prior to beginning anything else.

---

### Post by neer2005 on 2009-03-03
thanks i will try this and get back to you
the problem might be beacuase i am burning at 28x i will try a lower speed

---

### Post by neer2005 on 2009-03-03
i burned at 8x but still i get the same screen, I have wasted like 5 cds anyone with a solution!!!

---

### Post by avtolle on 2009-03-03
Did you check the md5sum of the iso before burning?

EDIT: [http://psychocats.net/ubuntu/iso#checksum](http://psychocats.net/ubuntu/iso#checksum) discusses how to do it from Windows; if you already have Linux installed, you can check it from the command line by```
cd Desktop
md5sum *nameoffile.iso*
```if the iso is on your desktop. This takes a bit to run. Once you get a result, you should compare it to the value for the particular iso shown at [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by neer2005 on 2009-03-03
Omg i love this forum i got it to work after reburning it at 8x

---

