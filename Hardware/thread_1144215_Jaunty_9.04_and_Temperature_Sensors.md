---
title: "Jaunty 9.04 and Temperature Sensors"
date: 2009-04-30
forum: Hardware
---

### Post by warnesey333 on 2009-04-30
Hi,

I've just recently installed a new motherboard - EVGA 790i ULTRA SLI FTW.

I've installed lmsensors and the sensor applet but it is displaying the system temperature at 83 degrees which got me worried.

The old edition of everest did the same but the new edition has changed and shows a much lower temperature.

I was wondering if there was a solution to this problem? Or maybe another piece of software for temperature monitoring?

Thanks

---

### Post by cariboo on 2009-04-30
Did you run :

```
sudo sensors-detect
```

in a terminal? You can try running:

```
sudo sensors -s
```

you won't get any output from the above command, but see if it makes a diference in you temp readings.

---

### Post by warnesey333 on 2009-04-30
Hi,

Yeah i tried that but nothing has changed.

Thanks

---

