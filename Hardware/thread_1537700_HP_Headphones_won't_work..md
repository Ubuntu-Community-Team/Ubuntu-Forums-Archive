---
title: "HP Headphones won't work."
date: 2010-07-23
forum: Hardware
---

### Post by blindbat1457 on 2010-07-23
So I just downloaded Mangler to connect to a Ventrilo server. I am connected to the server but my HP headphones won't work along with the microphone on it.

Not sure what version they but I bought them at Walmart for like 30 bucks.
I searched the HP site and Walmart and I can't find it.

[http://www.mysimon.com/shopping-picks/hp-premium-digital-headset](http://www.mysimon.com/shopping-picks/hp-premium-digital-headset)

I think those are it but not 100 percent sure since it is a small photo.
Could you please help me get them working :) Thanks.

---

### Post by blindbat1457 on 2010-07-24
Anyone?

---

### Post by lidex on 2010-07-25
Never heard of that software.
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

