---
title: "Dapper boots ok only one of each two times"
date: 2006-06-19
forum: Hardware &amp; Laptops
---

### Post by csk_73 on 2006-06-19
Hi there,

when I boot my laptop, it boots ok one of each two times, the other one freezes loading X and I have to turn it off, then next boot is ok.

Where can I begin the search?

The laptop is an HP Omnibook XT 1000. The graphics card is an S3.

Thanks

---

### Post by stimpsonjcat on 2006-06-20
your problem sounds similar to [this bug]("https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-savage/+bug/33617")

---

### Post by csk_73 on 2006-06-29
Hi,
it works!!!

thank you

I edited xorg.conf and added 

option "BusType" "PCI"
option "DmaMode" "None"

to the device section and then it stopped to get frozen

Thank you again

PD: And 3d acceleration has improved too! (not too much but is better than before)

---

