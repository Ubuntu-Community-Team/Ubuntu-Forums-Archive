---
title: "Firewire Digital Camera"
date: 2008-06-03
forum: Hardware
---

### Post by skeetwood-mac on 2008-06-03
how do I get my nikon d1h to work with ubuntu?? I plug it in and it doesnt recognize the camera. I tried gthumb and it doesnt recognize it either. Is it even possible? I remember when I first had hardy installed I would plug the camera in and ubuntu would recognize that something had been connected but I couldnt get at the pictures.

---

### Post by skeetwood-mac on 2008-06-03
bump!

---

### Post by skeetwood-mac on 2008-06-04
anyone?

---

### Post by lisati on 2008-06-04
Is your camera a stills camera or a video camera? If it's a stills camera, it might work better with USB instead of firewire.

---

### Post by skeetwood-mac on 2008-06-04
Its a still camera. How do I hook my firewire camera up to usb?

---

### Post by skeetwood-mac on 2008-06-05
bump?

---

### Post by skeetwood-mac on 2008-06-08
alright I installed coriander and tweaked a couple things and now it will open but it can't detect the camera. When I run gscanbus it says the camera is connected to the parent node. Any ideas?

---

### Post by skeetwood-mac on 2008-06-13
bump?!

---

### Post by galenanderson on 2009-03-07
> **skeetwood-mac said:**
> how do I get my nikon d1h to work with ubuntu?? I plug it in and it doesnt recognize the camera. I tried gthumb and it doesnt recognize it either. Is it even possible? I remember when I first had hardy installed I would plug the camera in and ubuntu would recognize that something had been connected but I couldnt get at the pictures.

I have the same problem, anyone who has used the D1h with linux could you please report how?

Thanks, Galen

---

### Post by chili555 on 2009-03-20
Have you tried plugging your CF card into a card reader and the reader into your computer? When I do so with either my old D70 or my D700, F-spot offers to download the photos and RAW files. I then manipulate them with Ufraw and Gimp. F-spot is probably already installed and the others are available in Synaptic.

---

### Post by |Porsche on 2009-04-20
I was having the same issue. dvgrab was telling me that no camera exists, and kino was not capturing anything. 

The problem was solved by doing a > sudo chmod 777 /dev/raw1394 and plugging the firewire cable to a different firewire port. I have 3 of them, and I plugged in to the one integrated into the motherboard.

I hope this helps.

---

