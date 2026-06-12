---
title: "HP Scanjet 4070 Photosmart Scanner"
date: 2007-03-07
forum: Hardware &amp; Laptops
---

### Post by JRevell on 2007-03-07
Hey,
I have a HP Scanjet 4070 Photosmart Scanner and it's not working.
So far, I've figured out it requires the hp3900 package for (x)sane.

Hmmm....

I installed it from a .deb, and at first it gave the error message about me not having permissions...
Then, I rebooted. Magically, it was nowhere to be found. I tried reinstalling the .deb, but now xsane just says that there is no device whatsoever.

Using the command "lspci," the scanner is nowhere to be found. Same as when I'm root.
Using the command "sane-find-scanner." No scanner found, even as root.
Using the command "scanimage -L." Not found normally, locks up as root.

Any help?

---

### Post by JRevell on 2007-03-07
*bump*

---

### Post by JRevell on 2007-03-08
*bump*

---

### Post by JRevell on 2007-03-08
help plz

---

### Post by timbosa on 2007-03-10
I'm assuming that you're connected by usb, I think that is the only option for this scanner so... what does ```
lsusb
``` give you?

---

### Post by *~Kat~* on 2008-01-14
I also have the same problem. I looked for the driver online and found it. Then I looked for the HP toolkit and tried to find the scanner through that and could not find it. There is a way to search for it manually and it tells me that to get the required information I have to use "lsusb", but I have no idea where to find it, far less to use it.

Can someone advise me on this, I'm still fairly new to Linux and am not yet knowledgeable enough in these things.

---

