---
title: "Lenovo ThinkPad SL510 bluetooth and webcam"
date: 2011-09-06
forum: Hardware
---

### Post by fomik on 2011-09-06
Hi,
I installed Ubuntu (11.04) on my laptop ThinkPad SL510, but unfortunately the bluetooth is not working (no device found). Also the internal webcam doesn't work. Is there anybody having this laptop with working bluetooth and webcam? I went through many documentation and at least webcam should work on this model with Linux as it's connected internally via USB.

---

### Post by fomik on 2011-09-07
According [https://wiki.archlinux.org/index.php/Lenovo_ThinkPad_SL510](https://wiki.archlinux.org/index.php/Lenovo_ThinkPad_SL510) at least webcam should work automatically, but it doesn't.
I tried the webcam with Cheese - it didn't find any video device. Then I removed module thinkpad_acpi, started Cheese again and it got frozen...

---

### Post by fomik on 2011-09-08
Regarding webcam: This UVC drivers discussion ([http://comments.gmane.org/gmane.linux.drivers.uvc.devel/5381](http://comments.gmane.org/gmane.linux.drivers.uvc.devel/5381)) says that the webcam is connected internally via USB. But the output of my lsusb doesn't show the device for me - I can see root hubs only:( What's wrong there?

---

