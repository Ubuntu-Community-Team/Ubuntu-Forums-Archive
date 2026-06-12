---
title: "Wireless switch not working properly-Vaio AR"
date: 2009-12-02
forum: Hardware
---

### Post by linuxgr on 2009-12-02
Hey all,

I tried to Google my problem but nothing, maybe I did not use the right keywords. Anyway:

Ubuntu 9.04
Sony Vaio AR825E
lspci:
```
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
```

The laptop has a hardware wireless switch.

If you start ubuntu with the switch set to "ON", everything works great, you can also turn it on/off and it works.

However, if you forget it to the "OFF" position and start the computer, there is no wireless and the switch is not responding.

I was wondering if there is some command I could run in order to fix this, because now I have to restart every time I forget the switch to "OFF".


Thanks!

---

### Post by hal10000 on 2009-12-02
I have the same network card on an amilo xi 2528 notebook.
I just tested the behaviour you described:

1.) I turned my network switch off and on again ----> it worked

2.) I switched it off and rebooted. After turning it on again ----> no wireless network was detected. 
But then i unloaded the iwlagn driver and reloaded it -----> it worked.

So i guess you don't have to reboot, you just have to reload the wireless driver:
```
sudo rmmod iwlagn
sudo modprobe iwlagn
```
But i don't know how to automate this. Maybe you also have to install the **wicd** package instead of that crappy network-manager.

---

### Post by linuxgr on 2009-12-03
hal1000, thanks a lot!
That's what I was looking for.

We can also put it in a small script and have it run anyway or run it manually whenever we forget the switch to "OFF".


Thanks again!!!!

---

