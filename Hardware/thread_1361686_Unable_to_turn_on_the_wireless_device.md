---
title: "Unable to turn on the wireless device"
date: 2009-12-22
forum: Hardware
---

### Post by francois203 on 2009-12-22
hi,
I'm new to Ubuntu, and I just installed version 9.10 on my HP Pavilion DV4-1125NR. However, I'm unable to turn on the wireless device and unable to connect to internet. Does anyone know why?

---

### Post by francois203 on 2009-12-22
I have a broadcom card. Is there any way to enable it in ubuntu without a wired connection?

---

### Post by Greenwidth on 2009-12-22
The driver might be on the CD (depends on what chipset you have)
Enable CD source in:
System > Admin > Software Sources

Then Check:
System > Admin > Hardware Drivers

---

### Post by francois203 on 2009-12-22
Actually i now have a wired connection. Does anyone have a simple solution to enable the card?

---

### Post by francois203 on 2009-12-22
Ok, now i was able to enable it, but im not able to connect to any network. Do you know why?

---

### Post by Greenwidth on 2009-12-22
Have you got enable wireless ticked when you right click the network icon?
Also did you put in the SSID and password for your network?

---

### Post by getanick on 2010-01-04
@ francois203

Hi. I have a similar problem as you had before, that is I am not able to enable wireless. I have hp-compaq nx-6325 laptop.
How did you solve your problem?

@ Greenwidth: Enable wireless option is not ticked in the network icon. It is somehow not tick-able in my case.

---

### Post by getanick on 2010-01-05
I could correct the problem. I just had to disable 'LAN/WLAN switching' option in the BIOS

---

### Post by Cabs21 on 2010-01-05
Had this same problem on my brothers Dell with Broadcom chip set.  After connecting to the internet via a wired LAN cable into my router I choose a driver in **System>Administration>Hardware Drivers** for the Broadcom wireless card.  After the wireless still didnt work I realized I had choosen the wrong card.  Do you know your wireless card chipset or model number.

what does ```
-iwconfig
```
output

---

### Post by LeslieL on 2010-01-05
I'm having this very same problem myself. I have an HP Pavilion dv2000 - a piece of plastic junk that does things like lose keycaps and shed bits and pieces from the guts of USB connectors. I upgraded to Karmic from Jaunty last week but found a few things not to my liking so did a full reinstall of it. After that I couldn't turn the wireless device on at all. I also saw repeated "Unable to enumerate USB device on port 1" messages on shutdown and startup. 

I have a Broadcom BCM4328 device. The Broadcom STA wireless driver shows up in the hardware drivers list as being activated but not in use. iwconfig says
> lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.



In the past my wireless has been eth1. It just doesn't show up at all now. 

I did everything in [this]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") very helpful document. No luck.

I'm beginning to think the device has physically failed. It wouldn't be surprising on this machine. But can anyone think of anything else I could try?

---

