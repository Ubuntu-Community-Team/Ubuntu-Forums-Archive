---
title: "Nvidia-glx"
date: 2005-09-12
forum: Hardware &amp; Laptops
---

### Post by KiCo on 2005-09-12
Im trying to get my 3d card to work. im im having some troubles with it.
I have msi nvidia geforce ti4200, and im trying to install nvidia-glx to get the card working but in install i get a error, and the install wont get true..

it says error (1), it cant write the info or something.. is there any manual way to get my card to work? ..

and second question.. I would like to play elastomania in ubuntu.. is there any
easy way to do it? ;D;D

thanks

KiCo
wicked.r8.org \\:D/

---

### Post by daller on 2005-09-12
Well, can you please post the error?

Normally you need to alter the content of /etc/X11/xorg.conf (sudo vi /etc/X11/xorg.conf)

(To edit anything with vi - press "i" when the file is opened - It will cause "---INSERT---" to show!!!)

Find this section:

---

Section "Device"
        Identifier      "Nvidia blah blah......................."
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection

---

You now have to replace "nv" by "nvidia" - In order to use the proprietary driver!

Good luck!

---

