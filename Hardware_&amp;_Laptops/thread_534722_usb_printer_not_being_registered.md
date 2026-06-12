---
title: "usb printer not being registered"
date: 2007-08-25
forum: Hardware &amp; Laptops
---

### Post by jefisme03 on 2007-08-25
ok so i have a 1018 lazerjet printer and i have proven that the usb ports i even checked the out put of the kernel and it shows communication between ubuntu and the printer but still i cannot get it to register after useing lsusb any thoughts? 


Aug 25 15:02:46 john-desktop kernel: [ 2123.340000] usb 2-6: device descriptor read/8, error -71

---

### Post by jefisme03 on 2007-08-25
bump because i hate that i have to boot windows to get this to work

---

### Post by jefisme03 on 2007-08-25
ok i think i have this figured out the hp lazerjet 10xx series must have the firm ware loaded onto the printer every time it starts up due to the fact that it has no non volatile ram so i need some one who can tell me how to force ubunto to upload the "nvram" into the printer

---

### Post by burns1111 on 2007-08-26
Hey there.  I had a similar issue with a Laserjet 1000.  Please check out this thread to find the answer that I found:

[http://ubuntuforums.org/showthread.php?t=220766](http://ubuntuforums.org/showthread.php?t=220766)

---

