---
title: "Conky CPU Temperature..."
date: 2008-10-30
forum: General Help
---

### Post by GmAz on 2008-10-30
I have an Asus P5N-E motherboard with an Intel Core2Duo CPU.  I don't think it is recording my temperature at all, unless my CPU hasn't moved in temperature for 2 days, is not registering properly.  Any suggestions?

Here is the portion of my conkyrc file that is for the temperature:
CPU Temp: ${acpitemp}C ${acpitempf}F

I had it on both C and F since it could have been a steady 40C, but the F shoudl have changed a little, but is still constnat at 104F

---

### Post by Spamwich on 2008-11-08
Have you tried using the *hwmon* variable?

I have an Asus P5B with an Intel Core2Duo E8400 and I get my CPU stats from this:

```
CPU Temperature: ${hwmon temp 2}°C CPU fan speed: ${hwmon fan 2} RPM
```

---

### Post by ufo_wam on 2009-12-11
Thx for the tip the hwmon object helped me display my core temp. However, I don't know why I had to put 01 as my sensor's number, despite that in my /sys/class/hwmon folder I have two folders named hwmon0 adn hwmon1. I guess that the first one is for the first core and so on. Neither 0 nor 1 seemed to work. They made conky crash for no apparent reason. If someone could get me some explanation it would be great :D

PS: I have the pavilion dv5 laptop (not really a good choice for intalling linux) with the t5800 core2duo 2.0Ghz processor.

---

