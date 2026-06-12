---
title: "[SOLVED] Lost scanner in upgrade to karmic 9.10"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by BigJules on 2009-11-05
If your scanner is not recognised by the koala when it worked perfectly well for the jackalope, its probably because it seems sane does things in 9.10 differently. 

Ensure your drivers are installed, the scanner powered up and run #lsusb or #sane find-scanner and it should come up there. For my trusty Brother lsusb said:

```
Bus 004 Device 002: ID 04f9:01e8 Brother Industries, Ltd
``` and for sane find-scanner:

```
found USB scanner (vendor=0x04f9, product=0x01e8) at libusb:004:002
```It means it's alive and well and could probably by xsane run as root, but this is a BAD IDEA (it will tell you, folks!)

Instead this info needs to be entered into the list of scanners in /lib/udev/rules.d/40-libsane.rules and for me I added the 2 lines:
```
# Brother DCP-7045N
ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="01e8", ENV{libsane_matched}="yes"
```[Note the id's lifted from before]
You'll probably need as well to get the permissions straight in /lib/udev/rules.d/50-udev-default.rules ; change the ‘ibusb device nodes’ line to ...MODE="0666"

And that's all it needs...

---

### Post by openzin on 2009-11-08
Thanks a lot!!! 
This is really working and noway to get such info from anywhere else. 
Oleg

---

### Post by manolomanolo on 2009-11-19
Those infos are reported here:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#6]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#6")

I've been asking Brother to put them in more evident places, such as in the general FAQ's pages (since the Linux specific Faq's are quite idden...)
and at the end of the driver installation instructions.

Please, would you mail(bomb) Brother too asking for more evidence/respect for Linux users?

Thank you.

---

### Post by sparks40 on 2009-11-20
Good to see that someone is making headway with this problem which seems to be affecting a lot of us.

I have a new twist on the same kind of issue. I am using an old Epson Perfection 610 which worked fine under Ubuntu 9.04. My problem is that when I have my Logitech Quick Cam Connect Sx video cam plugged into a USB port and my scanner plugged into a second USB port, I get the smae error message as mentioned previously. USB can't seem to differentiate between the scanner and the video cam. As soon as I unplug the video cam the scanner works properly. Under 9.04 both could stay connected to my motherboard at the same time without without a conflict. This sounds like a rules violation in udev. Is that possible and if so how can I correct it.

TNX

---

