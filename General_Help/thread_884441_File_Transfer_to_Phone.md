---
title: "File Transfer to Phone"
date: 2008-08-09
forum: General Help
---

### Post by Bbman90 on 2008-08-09
I have a MOTOROLA RAZR V3re. Whenever I connect it to my computer (via data cable), it begins charging the phone. However, I can't access it. Is there any way to "open" it in Nautilus as any other USB device? Can it be used as a drag-and-drop tool to transfer files between it and my computer?

---

### Post by mb_webguy on 2008-08-09
Check your phone's connection settings.  I have a Razr V3xx, and on my Settings->Connection->USB Settings menu, I have the options of Data Connection, Memory Card, Media Sync, and USB Printing.  If you select Memory Card, you should be able to access files on the phone as a USB storage device, and use Nautilus to drag-and-drop files to and from the phone.

---

### Post by Bbman90 on 2008-08-09
I do not have that menu on my phone. The only options are Bluetooth and Sync.

---

### Post by mb_webguy on 2008-08-09
What happens when you select Sync?

---

### Post by Bbman90 on 2008-08-09
I get the option to create a new entry, which can consists of a Name, URL, User Name, Password, and then Data Paths, Which can be Calendar and Address Book. Frankly, I have no idea what it is.

---

### Post by sdunatunga on 2008-08-16
Well I think you would have to use something like moto4lin or p2kc. However I haven't had any luck with those two programs with the same phone that you have (v3re). I eventually just grabbed the source of moto4lin and libp2kmoto (from trunk...) and am in the process of writing some programs to connect to the phone. It's going okay (I've been able to dump the entire contents of the phone to my drive, and write files to the phone) but I haven't gotten together a GUI or anything. It's all very basic at this point. I think there's a version of moto4lin that is supposed to be based on libp2kmoto in branch but that didn't work out for me either, despite the fact that I'm using the same backend :(. If you're interested in the source just PM me, but I warn you that it's pretty shoddy at this point.

---

