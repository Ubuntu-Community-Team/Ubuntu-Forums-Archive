---
title: "Laptop no longer detects USB mouse"
date: 2011-04-04
forum: Hardware
---

### Post by amanchesterman on 2011-04-04
I have a Toshiba Equium laptop which I have recently set up as a dedicated Linux machine (i.e not a dual boot). I installed Ubuntu 10.10 and a bunch of software, and everything has worked fine for the last week. Now the machine has stopped detecting the USB mouse.

I have tried starting and re-starting it with and without the mouse plugged in, and using different USB mice. I have searched the forums and read several threads, and learned from one of them that the command 'lsusb' shows the usb connections. On my machine each entry says 'Bus [number] Device [number] ID [number] Linux Foundation 1.1 root hub' (the numbers are different for each line of course). The entries don't change when I plug in or unplug USB mice.

However the usb sockets respond perfectly if I plug in a USB memory stick, and the entries in lsusb change accordingly. The touchpad works fine too.

At the time when this happened I was using a program (Filezilla) to update a website for which I am responsible. The Filezilla window on my screen was not large enough for me to see all the detail so I clicked on the 'maximise' button to enlarge it. The window expanded in the normal way and the mouse stopped working as described above.

Can anyone help me with some simple advice? I am new to Linux and simply don't understand a lot of the technical detail. Should I post this in 'Absolute Beginner talk' instead?

Thanks in advance

John

---

### Post by sanderj on 2011-04-04
When you plug in the USB mouse, does it's red light (under the mouse) turn on?

Does the USB mouse still work in other PC's?

When you do a CD live boot, does the mouse work?

---

### Post by amanchesterman on 2011-04-04
Hi, thanks for your response. The answers to your questions are:
- yes, the light under the mouse comes on when plugged in
- yes, the mouse works fine in another laptop
- I haven't tried booting from a live CD, that's my next step I guess.

---

### Post by amanchesterman on 2011-04-04
I have just restarted the laptop (the fourth time!) and the mouse now works fine. I guess this was just another instance of the recurrent USB mouse problem that is reported elsewhere in this forum, to which no one seems to have a solution yet.

Thanks for your help anyway.

---

