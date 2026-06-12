---
title: "display (X Server) problems with Fujitsu Lifebook FMV-650"
date: 2007-05-24
forum: Hardware &amp; Laptops
---

### Post by jon.reeve on 2007-05-24
I have a tiny Japanese Fujitsu Lifebook FMV-650, which as far as I know is a Japan-only model, so there's not a whole lot of info out there. Nonetheless, I don't particularly think the hardware is all that proprietary. I didn't seem to have to have a lot of extra drivers when I migrated from XP to 2000. Anyway, I've been getting a problem that says my X Server isn't configured correctly. 

```
(WW) VESA: No matching Device section for instance (BUSID PCI:0:20:0) found
(EE) No devices detected.

Fatal server error: 
no screens found
```

Could this have something to do with the fact that I installed this copy of ubuntu from my desktop pc, running the live cd and using the laptop's hd as an external hd? I'm worried that my laptop's OS now contains all the hardware config info for my desktop computer. 

Is there a way to simply autodetect all the hardware I have on my laptop? I appreciate the help, I'm in quite a beginner's bind here.

---

### Post by teaker1s on 2007-05-24
llets see what graphics you have
```
lspci | grep VGA
``` post result

then we can enter xserver and configure it
```

sudo dpkg-reconfigure xserver-xorg
```

---

### Post by jon.reeve on 2007-05-24
Thanks very much. It runs smooth as silk now. Hooray!

---

### Post by teaker1s on 2007-05-25
:popcorn:

---

