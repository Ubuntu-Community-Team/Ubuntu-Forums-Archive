---
title: "Sony  DSC-W70 doesn't work"
date: 2007-04-04
forum: Hardware &amp; Laptops
---

### Post by Kan_Kaiko on 2007-04-04
I have problems with importing photos form my Sony DSC-W70.
Nothing happened when I plugged it in so i typed lsusb in terminal and got:

Bus 005 Device 014: ID 054c:0010 Sony Corp. DSC-S30/S70/S75/F505V/F505/FD92 Cybershot/Mavica Digital Camera

I checked /etc/udev/rules.d/45-libgphoto2.rules and added lines:

# Sony DSC-W70
SYSFS{idVendor}=="054c", SYSFS{idProduct}=="0010", GROUP="plugdev", MODE="0660"

Then I ran /etc/init.d/udev restart
but still when I plug my camera in nothing happens. :( 

Can anyone help me, please?

Oh, and I'm using Ubuntu 6.06

---

### Post by bibci on 2007-06-29
Hi, I have a DSC-W35 and typyng lsusb I get your same string.
More, f-Spot and gThumb detect it as Sony DSC-F707V.
But nothin works.

Does anybody have ideas?

Thank you.
Ciao

---

### Post by unixhacker on 2008-04-05
its a camera issue. 

goto menu, setup page 2, USB Connect, select mass storage (instead of auto).

worked with my dsc-w35, other cams who have additional functionality over usb (like picturebridge etc.) will probably have the same issue of not beeing autorecognized by the system...

hope this helps

---

