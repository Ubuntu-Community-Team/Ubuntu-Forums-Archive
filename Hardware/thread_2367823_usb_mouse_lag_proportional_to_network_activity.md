---
title: "usb mouse lag proportional to network activity"
date: 2017-08-03
forum: Hardware
---

### Post by lothrail on 2017-08-03
Simple to replicate, start a torrent and mouse starts lagging, pause the torrent and it starts behaving normally.

---

### Post by Autodave on 2017-08-03
Could you please give us some specs on your machine and Ubuntu version you are running?  Is the mouse wireless?

---

### Post by lothrail on 2017-08-04
Xubuntu 17.04. Wireless mouse, standard cable mouse works without lags. I'm using standard kernel and wi -fi.
Also there's no lag on ethernet connection, only wi - fi.

---

### Post by Autodave on 2017-08-04
Since it only does it when the wifi is going strong for your download, I would say that the wifi for the mouse and internet are conflicting with each other. Why? No idea. Have you tried putting the mouse's receiver into another port? Maybe even extending the receiver away from the laptop a little to give it space from your built-in wifi for the internet by using a USB extension?

---

### Post by efflandt on 2017-08-07
Note that both WiFi and Bluetooth use the 2.4 GHz band, and laptops typically use the same antenna for both. Although, I think they may normally use somewhat different frequencies, so normally they do not interfere with each other. I don't know exactly what frequencies Logitech Unifying receivers use, but I have never had any problems with their wireless mice (other than having to use some electrical contact cleaner for M1 button switch used extensively for gaming).

Maybe your wireless mouse dongle is actually using WiFi frequencies. What manufacturer and model is the mouse, or what shows in output of **lsusb** for the USB receiver?

---

