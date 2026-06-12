---
title: "USB Shutdown during boot"
date: 2012-09-25
forum: Hardware
---

### Post by IlGala on 2012-09-25
Good morning everyone.
I uploaded a persistent live Ubuntu 10.04 LTS on a usb stick a little special. This key must be unlocked in advance through a pin pad and locks again after 30 seconds if is not used or if it loses power when plugged into the USB port.
Here the problems begin. During boot, the key is blocked and the first time I thought of a mistake or that the key was not well inserted, but the second attempt the same thing happens. After looking for more informations about what was happening I found that the USB ports lose power during a hardware check. I'm pretty profane what I write but apparently during boot it is ran a general check or something like that disables the USB ports and then enables them again. Now this is not a problem on normal USB flash drive, in my case means leaving suspended the boot, remove the key, unlock it and put it back again.

Can anyone help me to solve this problem? Is there any way to prevent them from being disabled the USB ports?

---

