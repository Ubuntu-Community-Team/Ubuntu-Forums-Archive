---
title: "NTFS USB-Harddrive"
date: 2006-09-14
forum: Hardware &amp; Laptops
---

### Post by cstadach on 2006-09-14
Hello everybody

I have a little problem with my ntfs formated usb harddrive.
When I power it up and plug it in an icon on the desktop appears and I am being asked if I want to explore the HD. Of course I do, why else would I plug it in. So I click yes but then kubuntu tells me that it cannot find the device.

After a few tryouts I realized that I am able to konquer the HD with root privileges.

Is there any way around this? I don't want whenever I plug it in to change into root mode.

thanks for the help
Christian

---

### Post by moore.bryan on 2006-09-14
*with the hd connected, open a terminal and travel to /media; your hd is probably put in as USBHD.  then ```
sudo chmod +x /media/USBHD
``` that fixed the problem for me.*

---

