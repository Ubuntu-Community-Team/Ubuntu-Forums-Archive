---
title: "Connecting Canon PowerShot SX200 IS doesn't work after kernel upgrade"
date: 2010-05-08
forum: Hardware
---

### Post by rbaleksandar on 2010-05-08
Hi :)

Note: Running 10.4 LTS with latest kernel

  I hope this is the right forum since the problem is concerning a piece of hardware. I have a digital camera **Canon PowerShot SX200 IS**. Before yesterday when I installed the new kernel, I had no problem with Ubuntu recognizing my camera. I plug the cable in the USB port and F-Spot starts showing me a nice view of all photos on the card that is inside my camera. Now nothing happens. It doesn't even appear as an unknown USB device. Nothing. I read about DigiKam and that it might solve such a problem, but it's for KDE. I'm using GNOME, so...

Any advice (except - buy a new camera :D) is appreciated.
Cheers,
rbaleksandar

---

### Post by IcarusR on 2010-05-08
Digikam will work in Gnome, when you install it with synaptic all the required kde libs are also installed.
But if it is not seen by the system then nothing will work.

Does it show if you run in  a terminal..

```
lspci
```

Is there anything relevant if you run 

```
dmesg
```

You could always try putting the card in a usb card reader.

---

### Post by rbaleksandar on 2010-05-10
Nope, it doesn't show. At least I couldn't find it (looked through all USB devices). I have a card reader of course. But when I want to transfer 5-10 photos, it's better to do that via direct connection PC<->CAM. It's said because the new Ubuntu brought me (for now) more disappointments and problems than it fixed things. WebCam is not working (in 9.10 it did work just fine) and dig.camera isn't working either (did in 9.10). I'll try a previous kernel. Hopefully it'll work...again.

---

