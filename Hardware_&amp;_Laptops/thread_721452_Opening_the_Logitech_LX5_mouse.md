---
title: "Opening the Logitech LX5 mouse?"
date: 2008-03-11
forum: Hardware &amp; Laptops
---

### Post by ironclaw on 2008-03-11
Does anyone know how to open the Logitech LX5 cordless optical mouse? I managed to remove the two top covers, and three screws (one more for the tilt wheel). The back of this last layer is now loose, but the front is apparently anchored onto something, and I'm not sure how to detach that.

One of the reasons I'm trying to open it up is to get to the tilt wheel and get rid of the clicking sound when I scroll, as well as just being curious :)

---

### Post by Vienna01 on 2008-04-08
Sorry no hardware help but I would  very much like to know what  the file /proc/bus/input/devices on your installation calls the LX5 mouse you have (assuming that you used that mouse with your install). 

To find out that please CAT /proc/bus/input/devices. The section I am interested in
will be the the one that has :
Name= <some type of mouse>

If you can find it please answer here or send me a private message. I am having a difficult time getting Gutsy to recognize my Logitech LX5 correctly. How your system saw the LX5 will help me debug my problem.

---

### Post by ironclaw on 2008-04-24
Sorry about this late reply, I didn't notice your message...

This is what /proc/bus/input/devices says about my mouse (well, the receiver connected by USB to the computer):
```
I: Bus=0003 Vendor=046d Product=c50e Version=0111
N: Name="Logitech USB RECEIVER"
P: Phys=usb-0000:00:02.0-4/input0
S: Sysfs=/class/input/input2
U: Uniq=
H: Handlers=mouse1 event2 
B: EV=20007
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143
B: LED=ff00
```

---

