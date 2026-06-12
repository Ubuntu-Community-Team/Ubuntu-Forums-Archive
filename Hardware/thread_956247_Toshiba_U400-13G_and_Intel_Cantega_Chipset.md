---
title: "Toshiba U400-13G and Intel Cantega Chipset"
date: 2008-10-23
forum: Hardware
---

### Post by dinamic78 on 2008-10-23
I try to install Ubuntu 8.04 Desktop onto my Toshiba U400-13G with no success, i will report on my travel to get Ubuntu onto this hardware into this thread...

Problems seems to be all chipset/video related 
(Intel Cantega with GMA X3100 graphics core)

This is what i stumble into:

- Normal installation results in mashed up display
  where xorg is using vesa driver
- Changing xorg.conf to use the Intel driver with
  same result as above
- Updated the Intel driver to v2.4 with no success
- Using VGA modes results in black screen

Found threads on this forum related to Intel Cantega, and Ubuntu 8.10 Beta should hav the latest drivers for this chipset, trying to install and the display problem is solved!!!

---

### Post by dinamic78 on 2008-10-23
Ok, i installed Ubunto 8.10 Beta, graphic problem is gone...

Started out to not having a WiFi driver, did an update using updatemanager
and voila i had a working WiFi...

Heres a list of verified components:

- Graphics / Compiz works like a charm
- WiFi Network works 
- Webcam works like a charm UVC based (verified with luvcview)

I'm very satisfied.. and waits for the 8.10 Release now..

---

### Post by Olnex on 2008-12-29
I have similar laptop (U400/H00), sometimes after resume from suspend, the screen's resolution becomes lower and I cannot reset it fro Screen Resolution as there is no that option.
Also, Mic (either internal or external) does not work, I'm using OpenSUSE 11.1 now and everything(except multimedia keys and bluetooth) seems to be working well.

---

