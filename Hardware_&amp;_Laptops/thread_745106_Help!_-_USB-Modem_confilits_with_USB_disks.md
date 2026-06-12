---
title: "Help! - USB-Modem confilits with USB disks"
date: 2008-04-04
forum: Hardware &amp; Laptops
---

### Post by falkTX on 2008-04-04
Conneting to internet using my USB-Modem was really hard to set, but now it works perfect, except one thing; I'll explain:
In order to use the USB-Modem I had to patch a system file so the USB-modem (that usually is recognized as a USB disk) gets "reloaded" and become a (usb-)modem.
But now, everytime i plugin my external HD, it won't open, and I have to delete the patch, reboot, use that HD, then apply the patch again and restart to acess web.

Is there a solution for me?

---

### Post by falkTX on 2008-04-11
Anyone??
Please,
I know you can help me...

---

### Post by fdimmling on 2008-04-11
Which USB modem? I'm using a Huawei E220 UMTS modem which also has a disk in it for the Windows driver installation. There is a small prog available to be run triggered by udev to make the modem available. This might be a better way compared to altering - which? - system files. You should really give more infos when asking for help.

Friedrich

---

### Post by falkTX on 2008-04-17
I use a MF622 from TMN, portugal.

Now I use a simple script I made to copy "15-ZTE-MF622.rules" to the udev directory, than I plug my USB, and after is connected, I have to run another script to delete that 15....rules file.

The problem is that my sisters sometimes use my laptop, and of course, they want net;

It would be nice an app that do the script things it for me, cause my sisters don't understand a bit of computers..

---

