---
title: "Connecting the Visioneer 7300 USB Scanner"
date: 2007-08-13
forum: Hardware &amp; Laptops
---

### Post by mlinchits on 2007-08-13
Hi, 
Does anyone know if the Visioneer OneTouch 7300 can be used in Ubuntu?
When I run SANE I get "failed to open device 'gtk68xx:libusb:002:003' Invalid argument."

I've installed quite a few programs/backends that seemed related to scanning through synaptic, but it did not help.

Thanks

---

### Post by linuxwizard on 2007-08-13
Yes it should work reported status good
[http://www.sane-project.org/sane-mfgs.html#Z-VISIONEER](http://www.sane-project.org/sane-mfgs.html#Z-VISIONEER)

Look over these
[http://www.meier-geinitz.de/sane/gt68xx-backend/](http://www.meier-geinitz.de/sane/gt68xx-backend/)
[http://www.sane-project.org/man/sane-gt68xx.5.html](http://www.sane-project.org/man/sane-gt68xx.5.html)


status good: means the device is usable for day-to-day work. Some rather exotic features may be missing.

---

### Post by mlinchits on 2007-08-14
So is this something that is supported automatically by Sane (i have the latest version installed or am I supposed to download some kind of patch?

thanks

---

### Post by linuxwizard on 2007-08-14
Those 2 links I didn't read them that close. 1 has documentation & configurations the other is a man page. I thought their might be something in them that would help you setup your scanner.

---

