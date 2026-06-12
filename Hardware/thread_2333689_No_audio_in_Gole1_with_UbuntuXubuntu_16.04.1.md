---
title: "No audio in Gole1 with Ubuntu/Xubuntu 16.04.1"
date: 2016-08-12
forum: Hardware
---

### Post by snok87 on 2016-08-12
Hi,

I just get a Gole1 device from Indiegogo and installed Xubuntu 16.04.1, i got no audio. HDMI is working without audio.

I got that: 

david@gole1:~$ lspci
00:00.0 Host bridge: Intel Corporation Device 2280 (rev 22)
00:02.0 VGA compatible controller: Intel Corporation Device 22b0 (rev 22)
00:03.0 Multimedia controller: Intel Corporation Device 22b8 (rev 22)
00:0b.0 Signal processing controller: Intel Corporation Device 22dc (rev 22)
00:14.0 USB controller: Intel Corporation Device 22b5 (rev 22)
00:1a.0 Encryption controller: Intel Corporation Device 2298 (rev 22)
00:1f.0 ISA bridge: Intel Corporation Device 229c (rev 22)
 
david@gole1:~$ aplay -l
aplay: device_list:268: no se encontraron tarjetas de sonido...

I dont know how to make it work.

---

