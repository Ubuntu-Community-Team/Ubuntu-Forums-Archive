---
title: "Changing default sound device"
date: 2005-03-01
forum: Hardware &amp; Laptops
---

### Post by TaNeK on 2005-03-01
Well, simple as that, I need to know how to change default device. Ubuntu for some reason sets my default to my usb webcam microphone, which is not desirable, as it suck at playing sounds (:P). Last time I had ubuntu, some nice guy told me a line I wrote in a terminal, and everything worked... Can't just remember what he told me to write :(.

Changing from hw1,0 to hw:2,1.

Thanks!

---

### Post by TaNeK on 2005-03-01
well, problem solved, with hepl from geppy.

sudo gedit /etc/esound/esd.conf
add -d /dev/dspX where X is the devicenumber, to default options, and restart esd. now just use esd and all is fine.

---

