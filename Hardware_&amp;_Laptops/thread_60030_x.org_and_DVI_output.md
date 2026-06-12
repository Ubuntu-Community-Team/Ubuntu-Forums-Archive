---
title: "x.org and DVI output"
date: 2005-08-26
forum: Hardware &amp; Laptops
---

### Post by napsy on 2005-08-26
I recently buyed a LCD monitor with analog and dvi output support. I ran dpkg-reconfigure xserver-xorg and set it up to the manufacter(samsung). If I use the analog cable it's all well but if I switch to DVI, there's no picture at all.

Is there a xorg command to switch to DVI mode? I'm ising ATI with DVI + analog outputs.

Greets,
Luka

---

### Post by John Nilsson on 2005-08-26
Do you get this problem if you start X with the DVI cable plugged and NOT the analog cable?

---

### Post by napsy on 2005-08-26
Hm. Yea, It works now. But the monitor freq is now only 60hz and I can't change it. If I try to force the freq with x.org, the monitor just automaticly sets to 60Hz. On the analog output I had 75 Hz and that's why this is so strange.

---

### Post by John Nilsson on 2005-08-26
[QUOTE=napsy]Hm. Yea, It works now. But the monitor freq is now only 60hz and I can't change it. If I try to force the freq with x.org, the monitor just automaticly sets to 60Hz. On the analog output I had 75 Hz and that's why this is so strange.[/QUOTE]
 Probably nothing to wory about. 60Hz should work fine. It's quite normal for a DFP.

---

### Post by tseliot on 2005-08-27
[QUOTE=napsy]Hm. Yea, It works now. But the monitor freq is now only 60hz and I can't change it. If I try to force the freq with x.org, the monitor just automaticly sets to 60Hz. On the analog output I had 75 Hz and that's why this is so strange.[/QUOTE]
DVI LCD monitors have 60 Hz refresh, it's a normal thing.

---

