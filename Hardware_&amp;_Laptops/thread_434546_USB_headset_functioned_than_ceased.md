---
title: "USB headset functioned than ceased"
date: 2007-05-06
forum: Hardware &amp; Laptops
---

### Post by vratnica on 2007-05-06
I v bought a new headset of .ednet, but as I took off the package I v read that it needs a windows OS

anyway, later I ve got this thing working, after I had to configure the  /etc/asound.conf where i set my usb headset as a default device (I have read the instructions on [http://seehuhn.de/comp/alsa](http://seehuhn.de/comp/alsa)) after i  took the number of card for my USB headset from /proc/asound/cards:

[HTML]0 [CMI8738MC6     ]: CMI8738-MC6 - C-Media PCI CMI8738-MC6
                      C-Media PCI CMI8738-MC6 (model 55) at 0xa000, irq 22
 1 [default        ]: USB-Audio - C-Media USB Headphone Set
                      C-Media USB Headphone Set   at usb-0000:02:03.2-2.3, full$
 2 [UART           ]: MPU-401 UART - MPU-401 UART
                      MPU-401 UART at 0x290, irq 5
[/HTML]

it worked than excellent. but last two times it ceased to work and I can hear through my headset nothing. 
I saw than that in my /proc/asound/cards the USB has somehow changed his card number. I changed it than in my /etc/asound.conf, too, but it hasnt helped. 

I have no idea how to proceede further...

anyone has?

thanx a lot!

---

