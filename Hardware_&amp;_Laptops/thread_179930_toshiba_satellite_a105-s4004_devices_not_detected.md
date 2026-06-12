---
title: "toshiba satellite a105-s4004: devices not detected"
date: 2006-05-21
forum: Hardware &amp; Laptops
---

### Post by dragonstw on 2006-05-21
k, so i'm installing this for the first time, and got problems.

 - x windows doesn't work.  i tried modifying /etc/X11/xorg.conf - either i didn't put the right stuff or it can't detect my devices.  so i'm just typing everything in this 640x480 terminal window.

 - i can't ssh into anything, so i'm assuming it doesn't recognize my wireless card and/or network.

 - when i run lspci, almost every entry says 
"xxxx:xx:xx kind_of_device : Intel Corp.: Unknown device 4_digit_number_in_hex (rev 02)"

 - so i tried to download the driver... w/o network access... so i tried it with a usb drive. /var/log/messages tells me that i "attached an scsi removable disk sdb at scsi2, channel 0, id 0, lun 0, type 0" but i can't find it.

 - on the other hand, if i look at /var/log/Xorg.0.log, it says that i'm loading the right driver, I810, for my Intel Graphics Media Accelerator 950 which (if i understand correctly, is part of the 945 express chipset).

i'm quite confused.  help?

3)

---

