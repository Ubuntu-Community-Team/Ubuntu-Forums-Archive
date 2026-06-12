---
title: "change polling rate for a wireless mouse:)"
date: 2007-07-08
forum: Hardware &amp; Laptops
---

### Post by __knk__ on 2007-07-08
hi all just bought myself a wireless mouse and keyboard set as the old mouse was doing some werd ****.  it's a ritmo one cant seem to find any model number on the box.  

anyway the mouse doesnt seem all that accurate, it's rated at 800dpi which i figure should be enough for me as i dont really play too many games and im not all that fussy.

i heard somewhere that changing the polling interval to a lower value can increase it precision but cant seem to figure out how to do this in ubuntu.   

thanks

---

### Post by __knk__ on 2007-07-09
ok i got it with

modprobe usbhid polling=2(or something like that - i was sure i used ht rite one tho)

 but didnt notice any difference and tried on my other mouse which seems to get a max of around 250 and set the pollingrate to about 20 tried 900 aswel for the hell of it and there was no difference in the latency.

ideas..

---

