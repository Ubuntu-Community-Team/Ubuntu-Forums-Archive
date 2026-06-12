---
title: "Software Switch"
date: 2008-04-29
forum: Hardware
---

### Post by scottuss on 2008-04-29
Hi everyone,

Just got fwcutter working for the wifi on my laptop, the driver shows up in restricted drives as in use and I have the device listed when doing ifconfig. 

Last time I used Ubuntu on this laptop there was something I had to type to get power to the wireless (there is no hardware switch, it's software and doesnt work on ubuntu) I cant remember what it was!

Does anyone know what I need to type to actually switch the card on?


Many thanks in advance

---

### Post by olejorgen on 2008-04-30
I'm not sure, but you could try:
```

for i in `find /sys -name "rf_kill" ; do echo 0 > $i ; done 

```
Maybe iwpriv, or iwconfig has something too

---

