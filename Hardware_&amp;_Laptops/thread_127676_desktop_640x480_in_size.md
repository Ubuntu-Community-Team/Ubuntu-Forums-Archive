---
title: "desktop 640x480 in size"
date: 2006-02-09
forum: Hardware &amp; Laptops
---

### Post by balicki on 2006-02-09
Hi there,
I'm a newbie on linux. I have an old NEC Versa sx on which I have installed Win 98 and Ubuntu breezy badger 5.10 (dual boot). But the problems I am having with linux are:
1. the full desktop size is 640x480 though the resolution is actually sharper. I have tried everything I find in the forum but nothing works for me. The graphic card is trident cyber 9388.
2. no sound, how can i install the sound drivers, I think the sound card is ES1978 Maestro 2E

Please can anyone help, Thanks in advance:cool:

---

### Post by Derek Djons on 2006-02-09
I took an look in the Synaptic Package Manager and it includes the 9xxx videocards of Trident. You should double-check if it's installed. If so you probably have to edit your /etc/X11/xorg.conf file, adding your maximal resolution.

---

### Post by mohapi on 2006-02-09
Just as a side note, I've found that occasionally the "detected" settings don't seem to work so well for my older hardware. 

Just as an example, I regularly have to knock down the color depth on my old Presario from 24 to 16 (in the /etc/X11/xorg.conf file), or the screen defaults back to 640x480 in 8-bit (?) color. Changing the default depth returns it to its proper resolution.

Anyway, just an idea.

---

