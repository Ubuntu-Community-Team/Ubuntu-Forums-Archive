---
title: "Please help"
date: 2008-01-31
forum: Hardware &amp; Laptops
---

### Post by W1ck3d on 2008-01-31
Hi
I m very new to linux i have very little experience with linux in laptops i have the following config 
HP COMPAQ PRESARIO B1801TU NOTEBOOK PC, INTEL PENTIUM M 760(2.0GHZ/2MB L2/533 MHZ FSB), 1GB  DDR2 RAM
i have installed the gutsy 7.10 every thing working quite nicely except my sound card i have got no sound at all can any one please help me with it.

---

### Post by yabbadabbadont on 2008-01-31
In a terminal window, run:
```
sudo lspci
```
Please post the output.

(this will help us determine the type of sound card used in the machine)

Edit: In case you don't already know, you can use your mouse to select the text from that window.  Then middle click to past it into your post here on the forums.

---

### Post by W1ck3d on 2008-01-31
> **yabbadabbadont said:**
> In a terminal window, run:
```
sudo lspci
```
Please post the output.

(this will help us determine the type of sound card used in the machine)

Edit: In case you don't already know, you can use your mouse to select the text from that window.  Then middle click to past it into your post here on the forums.

i have received the following output

PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
:confused:

---

