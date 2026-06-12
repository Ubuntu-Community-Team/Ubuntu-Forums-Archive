---
title: "Need plain xorg.conf file posted"
date: 2007-09-23
forum: Hardware &amp; Laptops
---

### Post by nuro305 on 2007-09-23
Hi,

Just installed for the 1st. time, dual boot with XP. Install went well but X won't start. I'm running an Alienware laptop with a nVidia Ge FOrce Go 7600 card.

It detected it correctly but the driver for it isn't available (I thought it would have downloaded it during install) The Live CD driver works fine for this card with no 3D. Can someone post a plain  xorg.conf  file I can use to get X running then I'll use the GUI to download the nVidia driver?

Whatever  xorg.conf  file the Live CD uses should work.

Thanks!

---

### Post by Cresho on 2007-09-24
why dont you just start up the terminal and run "sudo dpkg-reconfigure xserver-xorg"

---

### Post by w4ett on 2007-09-24
The restricted drivers are available:

System>Administration>Restricted Driver Manager........select the enable box and it will install the nvidia driver...you can then tweak your xorg.conf.

---

