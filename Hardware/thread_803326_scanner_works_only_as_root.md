---
title: "scanner works only as root"
date: 2008-05-22
forum: Hardware
---

### Post by kkkkdddd on 2008-05-22
I have Plustek UT12 scanner.

When I run "xsane" it says "No device found". 
When I run "sudo xsane" warning message is being displayed about that I am a root but then the scanner is found and it works.

It is also worth mentioning that, I am a member of "scanner" users group.

I guess that it a problem with some file permissions.

Could you help me?

---

### Post by conal on 2008-05-29
I have exactly the same problem with our new Canon lide 25 scanner with Xsane.

I always find permissions for devices to be a headache with linux, it really slows me down.

If anyone out there has any advice as to how you make all devices accessible all the time (without being root) that would be really helpful.

Many thanks

Conal

---

### Post by roy.nico on 2008-06-05
I have exactly the same problem with an AGFA snapscan 1212 Usb. 
I'm also looking forward to the solution...
Regards, 
Nicolas

---

### Post by earther on 2008-06-21
Same here with an old HP ScanJet 3000C.  Can only run as root even though user is a member of the scanner group.  Running Hardy 2.6.24-16-generic kernel on Gutsy, BTW.

No one has a quick fix?

---

### Post by roy.nico on 2008-06-23
Hi everybody

I solved this permission problem by editing the file "40-basic-permissions.rules" which is in  /etc/udev/rules.d/  as follows :

I replaced 0660 by 0777 in 2 places :

# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0777"
SUBSYSTEM=="usb_device",        MODE="0777"

I found this solution on [http://forum.ubuntu-fr.org/viewtopic.ph](http://forum.ubuntu-fr.org/viewtopic.ph) … 9#p1713659

Hope this helps others...

Nicolas

---

