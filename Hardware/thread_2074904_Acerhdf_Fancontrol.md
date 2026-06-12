---
title: "Acerhdf Fancontrol"
date: 2012-10-22
forum: Hardware
---

### Post by naja on 2012-10-22
Hallo,
I have managed to get acerhdf module to work in kubuntu 12.10 but i cant get the fan to stop, it goes to a slower state but it never goes off. I tried 1810tray in windows and it works very good and the Fan goes completly OFF and it gets faster as the temperatur rises.
my acerhdf.conf;
options acerhdf fanon=70000 fanoff=6000 interval=5  kernelmode=1 verbose=0 
I am suspecting that this is behavior started after some update, but i am not sure about that.
are there any other tweaks to make the fan go completly off?
thanks

---

### Post by naja on 2012-10-22
my acerhdf.conf is<
options acerhdf fanon=70000 fanoff=64000 interval=5  kernelmode=1 verbose=0 

thanks

---

