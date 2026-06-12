---
title: "tx1000 and hardy RESOLUTION problem!!"
date: 2008-06-23
forum: Hardware
---

### Post by beavermml on 2008-06-23
hi... i am very new to linux here

to make it short.... i clean install ubuntu hardy 8.04 tls and voila... got everything working ( except wireless n touchscreen which doesnt concern me much anyway )...

at first boot after the install...i dont have the resolution problem, stay at 1280 x 800 but after i install the nVidia driver using the restrited bla bla... and after reboot.. voila..
my screen resolution degraded to 640 x 480.. this doesnt happen to me when i clean install gutsy before..

any help.. i tried searching the forum but no luck ( basically tired of scrolling pages )

---

### Post by netvampire on 2008-08-12
go into the add/remove programs thing..can't remember what its called. remove anything and EVERYTHING related to nvidia and nvidia-restricted drivers ...

once they are gone do a fresh install of the latest nvidia drivers, or use envy to automate it for you.

what happens is when you reboot ubuntu the old restricted driver kicks in and overrides your recently installed driver. hope this helps.

---

