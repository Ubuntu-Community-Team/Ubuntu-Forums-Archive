---
title: "Setting the resolution on a Dell Inspiron 1100"
date: 2006-04-25
forum: Hardware &amp; Laptops
---

### Post by ssnitily on 2006-04-25
I've just installed Ubuntu 5.10 onto my throw around laptop and am stuck at 640x480. I've tried adjusting this but 640x480 is the only option I am allowed. I had a similar problem when installing windows on this laptop and a change of refresh rate fixed it but I am only offered 60hz in the Screen Resolution Preferrences window. This is my first foray into linux after being somewhat savvy in the windows world. Any help is greatly appreciated.

---

### Post by ssnitily on 2006-04-26
Found a link in another thread.
[https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell)

Foot -> Mouth :P

---

### Post by test on 2006-05-28
[http://www.ubuntuforums.org/showthread.php?t=183285]("http://www.ubuntuforums.org/showthread.php?t=183285")

---

### Post by ssnitily on 2006-05-31
Yeah I've tried all the different editings of xorg.conf that I could find, did the walk through with the 845 patch, no help what so ever. I'm pretty much just giving up.

---

### Post by durableapostle on 2006-06-01
Section "Monitor"
Identifier "Monitor0"
VendorName "Monitor Vendor"
ModelName "Dell 1024x768 Laptop Display Panel"
HorizSync 31.5 - 48.5
VertRefresh 59.0 - 75.0
Option "dpms"
EndSection

and in Section Screen, change the monitor line to read

Monitor "Monitor0"

---

