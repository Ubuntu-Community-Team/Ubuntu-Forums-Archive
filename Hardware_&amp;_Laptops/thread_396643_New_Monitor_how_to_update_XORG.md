---
title: "New Monitor how to update XORG?"
date: 2007-03-29
forum: Hardware &amp; Laptops
---

### Post by JimmyME on 2007-03-29
I just replaced my 17" LCD Samsung Syncmaster 770 with a 22" Samsung. 

Running an Nvidia 7900GS

The old monitor was set at 1280x1024, the new monitor's native res is 1680x1050.

XORG is still showing the old Syncmaster 770TFT settings.  How do I reinstall/reconfigure for the new monitor so XORG has the new monitors resolutions?

I tried sudo apt-get install nvidia-glx --reinstall  (didn't change anything)

I've done a lot of reading here but haven't found out how to reconfigure for a new higher resolution monitor.  System>Preferences>ScreenResolution only shows 1280x1024 as max res which was the 770TFTs max res

Thanks much!

Jim

---

### Post by taurus on 2007-03-29
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by JimmyME on 2007-03-29
Taurus, 

UDAMAN!

Thanks.  Selected Nvidia and 1680x1050 as only res choice, <ctrl><alt> backspace and Voila 1680x1050.

Jim

---

