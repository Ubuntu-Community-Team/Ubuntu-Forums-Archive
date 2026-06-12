---
title: "Connecting usb palm pilot"
date: 2006-01-08
forum: Hardware &amp; Laptops
---

### Post by zzaza on 2006-01-08
Hi Guys and Gals
Am unable to connect my usb palm tungsten t3 i messed up my /dev/pilot erased but i cant make a new one.
Looking at /var/log/messeges 
 visor 1-2:1.0: Handspring Visor / Palm OS converter detected
 usb 1-2: Handspring Visor / Palm OS converter now attached to ttyUSB0
usb 1-2: Handspring Visor / Palm OS converter now attached to ttyUSB1
usbcore: registered new driver visor
 drivers/usb/serial/visor.c: USB HandSpring Visor / Palm OS driver v2.1
      visor: loaded successfully
Can one help make with "S" link /dev/pilot
Thanks in advance

---

### Post by SuperCzar on 2006-01-08
i used the udev method to get my z22 working.

i cant find the instructions that i used but these look real close to what i was doing to make a new link.

[http://www.daniel-lemire.com/blog/archives/2005/12/10/using-a-usb-palm-pilot-with-udev/](http://www.daniel-lemire.com/blog/archives/2005/12/10/using-a-usb-palm-pilot-with-udev/)

-- SuperCzar

---

