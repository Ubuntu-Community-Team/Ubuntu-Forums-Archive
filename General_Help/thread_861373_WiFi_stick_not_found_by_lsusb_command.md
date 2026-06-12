---
title: "WiFi stick not found by lsusb command"
date: 2008-07-16
forum: General Help
---

### Post by groundnut on 2008-07-16
I had a fully functioning WiFi connection on my Ubuntu computer. Then I had to reset my BIOS for some other reason. Thereafter I could connect sometimes, but now the connection is totally lost.
What can I do to get my WiFi stick detected by the lsusb command?

kind regards,
Tony

---

### Post by hal8000 on 2008-07-16
If you dont see your wifi listed by the lsusb command, then its not being read or powered.

Unplug all other devices from the usb ports, then try your wifi dongle in another usb port, it may work again.

I've seen faults on computers where there simply hasnt been enough power on the usb ports to drive a wireless dongle. This can happen if there is a usb printer, webcam, scanner, memory card readers,etc
all drawing current from the usb ports.

---

### Post by groundnut on 2008-07-16
The WiFi stick is the only usb device I use for this machine.

I tried another usb port. This time the stick was recognized with the lsusb command. However no networks were visible an no connection could be made. Then I went back to the other port. Again not recognized. Thereafter I went back to the other usb port i tried. This time the stick was not recognized.

So apparently the stick can sometimes be read. But there is something unstable.

May be something was destabilized by the BIOS reset.

Any suggestions?

kind regards,
Tony

---

### Post by coffeecat on 2008-07-16
Are you using usb ports at the front or the back? If at the front, check that the cable from the case usb ports is seated in the motherboard usb headers properly. If there is another set of headers, try plugging the cable into those instead.

If you are using the rear usb ports, they are part of the motherboard and you can ignore this post. :wink:

---

### Post by groundnut on 2008-07-16
Before the BIOS reset I used the a port at the front. No problem.

Now it's at the rear because for a while the stick was read with lsusb.

kind regards,
Tony

---

