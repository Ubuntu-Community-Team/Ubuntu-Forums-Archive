---
title: "external keyboard not working, dell inspiron 9300"
date: 2005-08-18
forum: Hardware &amp; Laptops
---

### Post by kingbanditjing on 2005-08-18
dell inspiron 9300
ps2 m$ external keyboard with usb converter

It works fine on my gentoo desktop, but not on the ubuntu laptop.

any ideas as to what might be causing this?  i can't find any mention of it being detected in the logs..  what logs should it be in anyway?

thanks...

---

### Post by s_p_a_r_k_y on 2005-08-19
dmesg is the command to use when seeing what kernel messages are genereated. to get the last few lines after you plugged it in, type dmesg | tail

and it'll give the last messages I believe. You may need to have usb modules loaded, especially ones which are related to human interface devices (HID)
```
 sudo modprobe usbhid 
```

---

