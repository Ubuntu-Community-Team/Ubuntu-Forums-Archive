---
title: "ELAN Touchscreen Issue"
date: 2014-05-28
forum: Hardware
---

### Post by faust2 on 2014-05-28
Hey bros, I have Dell Inspirion 15 with an ELAN Touchscreen, the Touchscreen never worked right, it randomly attacks the screen tries to click all the things and such. Normally I just disable it. I recently ported over to Ubuntu after using Windows 8 (Subsequently 8.1) for a while for school, I've loved ubuntu since 8.04 LTS and have used it or some flavor of Linux whenever possible. 
reen
In 13.10 I had no issues with the Touchscreen enabled, I figured maybe the issue was with Windows (Hah, surprising...) and after my upgrade today to 14.04 LTS the Touchscreen has gone nuts again. 

I've made the following attempts but to no avail: 

Ran xinput -disable "ELAN Touchscreen" 
-Disables it for a few seconds then it's back causing havoc. 

Ran dconf-editor 
-Only Touchscreen option is for enabling orientation lock

Ran sudo echo -n "1-1.2" > sudo tee -a /sys/bus/usb/drivers/usb/unbind
- Command didn't return any errors, but the touchscreen remains enabled. 

I'm a writer, I can live without the Touchscreen I never really used in the first place, I can't live with this frustration though :O

Help me UF! You're my only hope!

---

### Post by faust2 on 2014-05-29
After hours of poking around I finally found this workaround : [http://ubuntuforums.org/showthread.php?t=2209083&highlight=disable+touchscreen](http://ubuntuforums.org/showthread.php?t=2209083&highlight=disable+touchscreen)

Hope it helps everyone else who encounters this or a similar issue. Marking this is resolved/fixed. This may be closed if necessary. Thanks anyway, guys!

---

