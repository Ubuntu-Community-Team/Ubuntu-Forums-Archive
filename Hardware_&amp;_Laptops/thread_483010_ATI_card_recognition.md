---
title: "ATI card recognition"
date: 2007-06-24
forum: Hardware &amp; Laptops
---

### Post by circuitburn on 2007-06-24
Ok, first off I am completely new to the linux game, and many things are not quite clear to me. My Satellite A70 has a Radeon 9000 IGP card, but when I run the Hardware Information manager it lists the video card as a 9100. I'm not sure how different the two devices are, if there is any difference, but I was wondering how to go about getting the right drivers and card info in there. I have noticed several glitches when it comes to video, namely the screen partially blacking out and the desktop effects becoming choppy occasionally. 

Thanks in advance,

CB

---

### Post by ukripper on 2007-06-24
If you go to terminal and type the following command and paste the output here -

```
sudo gedit /etc/X11/xorg.conf
```

---

