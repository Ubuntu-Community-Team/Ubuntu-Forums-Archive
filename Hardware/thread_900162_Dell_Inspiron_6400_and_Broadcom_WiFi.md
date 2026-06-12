---
title: "Dell Inspiron 6400 and Broadcom WiFi"
date: 2008-08-25
forum: Hardware
---

### Post by Ronentrop on 2008-08-25
I have done a clean install from the Release Party CD, so nothing else than Ubuntu 8.04 is on my harddisk.
Alle works except my WiFi card. I have copied the firmware files to the firmware directory with *sudo cp *.fw /lib/firmware*. When I go into the firmware directory I can 'see' the files but they all have a flag "unreadable"?
There is a little WiFi indicator on the LapTop that used to light up under Windows and also when I had a dual boot with XP. Now it doesn't even light up.
Any idears?
Thanks,
Ron

---

### Post by Ronentrop on 2008-08-25
OK, now I have the WiFi indicator back working. It seems that the firmware files need to be in a subdir of /lib/firmware!

However I cannot find any wireless networks? Have used WiFi-radar and KWiFiManager. Both did not give me a network to connect to?

Any idears,

Ron

---

### Post by Ronentrop on 2008-08-26
Problem is solved!!

When tried using the function key combination Fn+F2 (start/stop WIFI) my network appeared in the Radar. The indicator stays on so........

---

