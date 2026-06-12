---
title: "ipw2200 wlan with ndiswrapper"
date: 2005-04-23
forum: Hardware &amp; Laptops
---

### Post by abdulsalam on 2005-04-23
hi all now  im using the driver that comes  with ubuntu for the wlan card ipw2200bg,
it work's great with my HP laptop.but the blue light dont work when the card is on,so i decided to use ndiswrapper with windows driver .
how can i do that?do i have to delete the ipw2200bg driver that comes with ubuntu first.

regards

---

### Post by flipy on 2005-04-24
[QUOTE=abdulsalam]hi all now  im using the driver that comes  with ubuntu for the wlan card ipw2200bg,
it work's great with my HP laptop.but the blue light dont work when the card is on,so i decided to use ndiswrapper with windows driver .
how can i do that?do i have to delete the ipw2200bg driver that comes with ubuntu first.

regards[/QUOTE]
 first, I don't think using the windows drivers solve the led thing (I've tryed the same drivers on a Asus A5S).
It has to be something like /proc/drivers/net/wled (mind me, I don't know the exact path, do some googleing) and change the state from 0 to 1.

---

### Post by luca_linux on 2005-04-24
The driver has nothing to do with the led. In order to control the light you have to create a script that echoes "1" to the wled file in /proc/acpi/...

---

### Post by abdulsalam on 2005-04-24
thank you for your reply
as i tryed to use ndiswrapper with Linux yoper and the led worked.
i locked in /proc/acpi,net,driver but could not find the stat value.
so i think it's easer for me to use ndiswrapper with win driver.
but could you please tell me if i have to delete the driver that comes with Ubuntu,
to avoid any conflect.

---

