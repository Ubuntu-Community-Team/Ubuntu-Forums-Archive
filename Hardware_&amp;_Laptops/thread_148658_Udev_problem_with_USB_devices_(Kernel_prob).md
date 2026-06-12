---
title: "Udev problem with USB devices (Kernel prob)"
date: 2006-03-22
forum: Hardware &amp; Laptops
---

### Post by pksings on 2006-03-22
No /dev/tts/USB* or /dev/ttyUSB* is created when the device is connected and sync initiated.  

Previously the modules "visor" and "usbserial" were inserted automatically when this occurred. 

Manually inserting them generates log messages but no devices.

I had the same problem with my Gentoo box at home and adding them as into the kernel solved it, (I chose not to have them as modules).  So this appears to me to be a kernel issue, please feel free to correct me if I'm wrong.   

This behavior began after the most recent kernel upgrade...

Thanks in advance.

PK

---

