---
title: "No-CD-ROM/Live USB Install.  How to mirror a CD-ROM drive for installation purposes?"
date: 2007-12-10
forum: Hardware &amp; Laptops
---

### Post by casacerian on 2007-12-10
I recently installed Ubuntu onto my Toshiba laptop (A-70-ish, non-functional cd-rom) via live install from a USB device. Most things work properly, however some installations require access to the live CD. This is not possible as my CD-ROM drive does not function, and when I insert the USB device I installed Ubuntu 7.10 from; I recieve a failure to mount error from the USB.

There is a CD ROM 1 listed in my system, however it has no proper pathing in its properties <(/computer:::)(Volume:/)>. It also has an identical amount of free space as my Ubuntu partition.

This problem is crippling due to my lack of in-depth linux/Ubuntu knowledge. I cannot properly install certain drivers, and get past certain copy protections that require a check of the CD-ROM or installation of additional resources from the CD-ROM.

If someone has ideas please post here. If there is specific information I can provide that will help resolve this, again, please post what you want to know.

Thanks in advance.

---

### Post by Craigus on 2007-12-10
Is this machine not connected / able to be connected to the internet ?

---

### Post by casacerian on 2007-12-10
It is connected via cat-5 cable. 7.10 and wireless do not seem to belong in the same sentence together yet.

---

### Post by ilrudie on 2007-12-12
Your problem is most likely that you have the Gutsy LiveCD listed in your software sources.  Open "Software Sources" from System>Administration.  You will see "Installable from DVD/CD-rom" near the bottom of the first tab.  Unselect both CD's from this list and it should download the files instead of looking at a for the CD.

---

### Post by casacerian on 2007-12-14
Fixxed. Cheers.

---

