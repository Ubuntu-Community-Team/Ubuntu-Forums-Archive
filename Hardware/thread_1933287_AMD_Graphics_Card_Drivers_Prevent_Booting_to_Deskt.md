---
title: "AMD Graphics Card Drivers Prevent Booting to Desktop"
date: 2012-02-29
forum: Hardware
---

### Post by SamBam77 on 2012-02-29
I tried installing the drivers for the AMD video card using instructions found here:
[http://help.stedman.net.au/2012/02/more-xubuntu-1110-on-hp-dv6-6023tx.html](http://help.stedman.net.au/2012/02/more-xubuntu-1110-on-hp-dv6-6023tx.html)
for my HP dv6t Quad 6000 series notebook with an AMD 7470M discrete graphics card.

However, after rebooting X fails to load and I cannot get anything graphical to work on the computer. I can boot into recovery mode, but I cannot load X or any graphical programs. If I boot normally it will just hang indefinitely at a screen with a list of tasks that it is trying to do with &#8220;[OK]&#8221; next to most of them, though it &#8220;[fail]&#8221;s on &#8220;Starting automatic crash report generation&#8221;.

How can I reverse the damage I have done (uninstall the drivers, etc&#8230;) so that I can get the computer back to a useable state?

---

### Post by elliotn on 2012-02-29
> **SamBam77 said:**
> I tried installing the drivers for the AMD video card using instructions found here:
[http://help.stedman.net.au/2012/02/m...v6-6023tx.html](http://help.stedman.net.au/2012/02/m...v6-6023tx.html)
for my HP dv6t Quad 6000 series notebook with an AMD 7470M discrete graphics card.

However, after rebooting X fails to load and I cannot get anything graphical to work on the computer. I can boot into recovery mode, but I cannot load X or any graphical programs. If I boot normally it will just hang indefinitely at a screen with a list of tasks that it is trying to do with “[OK]” next to most of them, though it “[fail]”s on “Starting automatic crash report generation”.

How can I reverse the damage I have done (uninstall the drivers, etc…) so that I can get the computer back to a useable state?

try to remove the file nvidia-common and and other NVIDIA related file and reboot

---

### Post by Yellow Pasque on 2012-02-29
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

---

