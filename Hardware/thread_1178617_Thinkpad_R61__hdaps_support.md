---
title: "Thinkpad R61  hdaps support"
date: 2009-06-04
forum: Hardware
---

### Post by la_monda on 2009-06-04
I tried to install hdaps using the guide i found for jaunty from here:
[http://www.nowhere.dk/articles/tag/hdaps](http://www.nowhere.dk/articles/tag/hdaps)

when i type: sudo modprobe hdaps i get this:
FATAL: Error inserting hdaps (/lib/modules/2.6.28-11-generic/kernel/drivers/hwmon/hdaps.ko): No such device or address

again when i type: dmesg| tail
dinos@dinos-laptop ~ $ dmesg| tail
[  554.485609] hdaps: driver init failed (ret=-6)!
[  569.856361] hdaps: inverting axis readings.
[  569.856367] hdaps: LENOVO ThinkPad R61 detected.
[  569.856374] hdaps: driver init failed (ret=-6)!
[ 1077.839606] hdaps: inverting axis readings.
[ 1077.839613] hdaps: LENOVO ThinkPad R61 detected.
[ 1077.839620] hdaps: driver init failed (ret=-6)!
[ 1228.834826] hdaps: inverting axis readings.
[ 1228.834833] hdaps: LENOVO ThinkPad R61 detected.
[ 1228.834840] hdaps: driver init failed (ret=-6)!

Any suggestions anyone???

---

### Post by rCXer on 2009-06-04
Maybe tring a differnt set of instructions will work.  I recently installed hadps on my Thinkpad T43p using [this guide](http://www.thinkwiki.org/wiki/Installing_Ubuntu_9.04_(Jaunty_Jackalope)_on_a_ThinkPad_T61#Enabling_Active_Protection_System).

---

