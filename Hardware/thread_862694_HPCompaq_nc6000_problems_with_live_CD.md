---
title: "HP/Compaq nc6000 problems with live CD"
date: 2008-07-17
forum: Hardware
---

### Post by Nospunosaj on 2008-07-17
I recently acquired a used HP nc6000 and I can't get the Ubuntu live CD (8.04 and 7.04) to function properly. When I try to boot the live CD, the Ubuntu load splash goes on for awhile and then goes black with a blinking cursor.

Awhile later, this error pops up twice:
Buffer I/O error on device fd0

I have waited beyond this point and the live CD eventually continues booting, but it's the slowest I have EVER seen a live CD boot. 

If you're patient enough, the desktop begins to show up, very slowly, and then an error about the GNOME settings daemon not initializing appears.

I have waited almost an hour on this process twice, and have nearly reached a fully functional live CD. But as soon as you try to do anything on the desktop, like start the installer or run Firefox, the session crashes.

Anyone have an idea what might be going wrong?

Here are my specs:
HP nc6000
Intel Centrino 1.7 GHz
256 MB RAM
12GB IBM Travelstar HD (The same problem occurs with or without the HD)
Wi-Fi functions well if you get far enough in the live CD to see it.
ATI Radeon Mobility 9600 32 MB
Generic 24x CD-ROM

---

### Post by PRMan on 2008-07-17
You can't use the Live CD with 256MB of RAM.  It requires about 350.

Use the Alternate Install CD instead.  It uses a text-mode installer.

---

### Post by Nospunosaj on 2008-07-18
I will try that. Thanks!

---

