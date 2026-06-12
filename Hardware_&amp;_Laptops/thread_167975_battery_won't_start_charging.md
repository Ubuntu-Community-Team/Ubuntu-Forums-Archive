---
title: "battery won't start charging"
date: 2006-04-29
forum: Hardware &amp; Laptops
---

### Post by feersum_endjinn on 2006-04-29
Hi, 
I've recently installed ubuntu on my packard bell es3250.

I have a problem it seems with ubuntu starting a charge on my battery. I've looked at other posts and I haven't noticed anyone with the same problem. When i use 'hal-device-manager' to look at the battery and ac details everything is working properly, ie unplugging the ac cause the battery to start discharging, pluggin it in stops it discharging etc, but there is the line 'battery.rechargeable.is_charging bool false'. Is it possible to manually edit this line so it has boolean value true? I know that the battery is in pretty good shape, it worked fine before I installed ubuntu and used it's first charge up, now it won't even charge under windows!

Very grateful for any help,

cheers,

G

---

### Post by bflores on 2006-05-05
Those notebooks do not come with a battery stop.  Hence when the battery is full the system still tries to run power to the battery.  This common with HP's and compaq's as well.  It will enventually burn out the charging curcuit on the mainboard.
This not show up on the os the operating system will continue to try to charge the battery even when to is no path for the battery to actually charge.

---

