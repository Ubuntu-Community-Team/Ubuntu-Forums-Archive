---
title: "Can't load IPW2200 firmware after upgrade from Warty"
date: 2005-04-04
forum: Hardware &amp; Laptops
---

### Post by adamvert on 2005-04-04
Hi

I just updated my Toshiba Satellite M30 Centrino from Warty to Hoary, and now I can't load the ipw2200 module anymore - there seems to be a problem loading the firmware.

The upgrade radically reduced my lovingly created /etc/modules list (I didn't realise that was going to happen, it would have been nice to have had a chance to back it up ), removing the ipw2200 among others.  Now when I do 

> modprobe ipw2200 

there is no output, but checking the syslog reveals:

```
ipw2200_boot.fw load failed
Unable to load firmware: 0xFFFFFFFE
failed to register network device
probe of 0000:02:0a.0 failed with error -5
``` 

/lib/hotplug/firmware contains ipw2200_boot.fw-2.6.8.1-4-686, which is the correct firmware for my kernel version.

Does anyone have any ideas how to get the firmware to load properly?  I was all excited about updating to Hoary, but now I'm reduced to sending this on my girlfriend's Mac... :-( 

TIA,
Adam

---

### Post by jerome bettis on 2005-04-04
sudo cp /lib/hotplug/firmware/* /usr/lib/hotplug/firmware

---

### Post by adamvert on 2005-04-04
Actually I fixed it by updating to the 2.6.10 kernel.

Now if I look in the /lib/hotplug/firmware directory I have extra entries for the 2.6.10 versions, but the name format is slightly different:
```

ipw2200_boot.fw-2.6.8.1-4-386
ipw2200_boot.fw-2.6.8.1-4-686
ipw-2.2-boot.fw-2.6.10-5-386
ipw-2.2-boot.fw-2.6.10-5-686

```
Could that be the problem?- that the ipw2200 module was looking for the wrong filename?

And still /*usr*/lib/hotplug/firmware is empty... I don't really understand, but it doesn't matter because it works now :)

Adam

---

