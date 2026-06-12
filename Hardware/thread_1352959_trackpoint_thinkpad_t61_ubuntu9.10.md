---
title: "trackpoint thinkpad t61 ubuntu9.10"
date: 2009-12-12
forum: Hardware
---

### Post by mikecarlone on 2009-12-12
hi everyone, the trackpoint was working with ervery version of ubuntu. i never had a problem, because i was doing what to need in order to work it. and now i think after i installed gpointing setting device had problem. now after turning off the laptop the settings in configure trackpoint are default. also the sensitivity and the speed of trackpoint are very slow.
rc.local, sysfs.cnfg also added to startup, but no success yet.

how can i solve this problem

thx.

---

### Post by mikecarlone on 2009-12-12
no help for me :(

---

### Post by mikecarlone on 2009-12-13
i also added the settings

echo -n 255 > /sys/devices/platform/i8042/serio1/serio2/sensitivity
echo -n 255 > /sys/devices/platform/i8042/serio1/serio2/speed
echo -n 1 > /sys/devices/platform/i8042/serio1/serio2/press_to_select


to rc.local but no success yet.i dont know why. for 3 years i have been using it and suddenly it doesnt work .

i realy dont know why its so. i did every thing but it always fails. if i restart the laptop it work. or if i turn off the laptop and turn on in 2,or 3 seconds again it works. but if i turn it off and wait 10 seconds or more it doesnt work anymore???

any help for me ??? in other case i muss  reinstall ubuntu.9.10

---

### Post by prokher on 2010-12-09
Looks like I have the same issue, at least very close one. I cannot configure trackpoint on my ThinkPad X200s as well. It's extremely slow. And editing rc.local don't help as well. As for me I don't see any correlations between that malfunction and time which laptop spend swiched on or off. It just works sometimes but more often it doesn't.

Similar thread: [http://www.newyork.ubuntuforums.org/showthread.php?p=10220469#post10220469](http://www.newyork.ubuntuforums.org/showthread.php?p=10220469#post10220469)

---

