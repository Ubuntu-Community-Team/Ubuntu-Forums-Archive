---
title: "how can I get a Temperature readout in terminal or ubuntu?"
date: 2008-10-04
forum: Hardware
---

### Post by asnd16 on 2008-10-04
Exactly what the title says, HOW? and how can I edit the shut off limit.

---

### Post by jerome1232 on 2008-10-04
For just a basic display of temps on your panel you can install sensors-applet, you can add it to your panel just like any other applet (right click->add to panel) You can also add alarms to it.
```
sudo apt-get install sensors-applet
```

As for setting up a shut off limit I've always just done this in my BIOS, if your motherboard doesn't support that I know programs exist to help with that but like I said I go the hardware route so I don't know which/what is good and how to config them.

---

### Post by asnd16 on 2008-10-04
yeah cool thanks man . . I think 102 c it will shut the computer down.  Which is about 212f.

---

### Post by kerry_s on 2008-10-04
> **asnd16 said:**
> yeah cool thanks man . . I think 102 c it will shut the computer down.  Which is about 212f.

make sure you install lm-sensors and run> sudo sensors-detect
to get the most out of sensors-applet. then you can pick what you want to monitor.

---

### Post by The MAX on 2008-10-07
I ran this exactly

> sudo apt-get install sensors-applet lm-sensors
sudo sensors-detect


and it only detected my 8800 GT card temp. When I should have a CPU and mobo temp sensor as well

Mobo = P5Q-Pro
CPU = Intel Core 2 Duo E8400 3.0 GHz

any ideas?

---

### Post by The MAX on 2008-10-08
anyone?

anyone?

Beuler?

---

### Post by blackpaw on 2008-11-24
Hi!

This seems to be related to the Motherboard..or the sensors chip - I have the same issue, somehow only GPU is detected.

Looking around the interweb a little I found this article on a gentoo board:
[http://article.gmane.org/gmane.linux.drivers.sensors/17253]("http://article.gmane.org/gmane.linux.drivers.sensors/17253")

He basically got the P5Q-E sensors running.
You could check if the P5Q-Pro is using the same winbond chip as the P5Q-E (W83667HG) and then just try it out. 

Will try this tonight :)


Andreas

---

### Post by blackpaw on 2008-12-01
I can confirm the sensors-applet works properly now after the above mentioned manual poking of the sensor chip (the "modprobe" part..) It is now showing my GPU's temp, the fans and all four cores' temp. properly.

Andreas

---

