---
title: "Laptop wont boot with Wireless turned off?"
date: 2007-02-09
forum: Hardware &amp; Laptops
---

### Post by Loonux on 2007-02-09
Im running kubuntu 6.10 and if I turn off my wireless before I shutdown, the next time I boot into linux it fails to load, moaning of a &#8220;soft lockup on cpu #2&#8221;. I then have to remove the battery, power the machine back up, boot into Windows to turn on the wireless (there is no hardware switch, its controlled via a function key on my dell 6400 which has no effect in the BIOS) and then reboot.

Is there anything that can be done to overcome this rather major flaw in the software?


Thanks

---

### Post by torst on 2007-03-30
I have the same problem with my HP Pavilion 9038ea notebook. It has a killswitch on the front for the radio frequency (built-in WiFi card), and when it is turned off, I as well get almost the same message (soft lockup on cpu #0 instead of 2 )and the laptop won't boot. There are more people out there with the same problem I have noticed when searching around.
[http://www.stuvel.eu/archive/37/bug-soft-lockup-detected-on-cpu0](http://www.stuvel.eu/archive/37/bug-soft-lockup-detected-on-cpu0)

My kernel version: 2.6.17-10 generic

Computer hardware spec:
[http://h10010.www1.hp.com/wwpc/se/sv/ho/WF06b/23355-186369-1291457-1291457-1291457-12435600-77989731.html?jumpid=oc_R1002_SESVC-001_HP%20Pavilion%20dv9038ea%20Notebook%20PC&lang=sv&cc=se](http://h10010.www1.hp.com/wwpc/se/sv/ho/WF06b/23355-186369-1291457-1291457-1291457-12435600-77989731.html?jumpid=oc_R1002_SESVC-001_HP%20Pavilion%20dv9038ea%20Notebook%20PC&lang=sv&cc=se)

---

