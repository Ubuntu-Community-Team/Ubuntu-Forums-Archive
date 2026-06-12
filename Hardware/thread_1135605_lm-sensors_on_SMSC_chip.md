---
title: "lm-sensors on SMSC chip"
date: 2009-04-24
forum: Hardware
---

### Post by ProNux on 2009-04-24
Hi there,

I have Ubuntu Jaunty on Dell Optiplex 170L.  I tried installing lm-sensors, run "sensors-detect", and at the end, here's what I got...

#----cut here----
# Chip drivers
# no driver for SMSC LPC47M172 Super IO Fan Sensors yet
#----cut here----

It's clear the error means no driver yet.  Anyone have a direct instruction on how to install?  I am still searching the net besides asking for help.  Thanks...

---

### Post by schitthoch2 on 2009-12-23
Is there any progress in activating the chip?
```

Trying family `SMSC'...                                     Yes
Found `SMSC LPC47M172 Super IO Fan Sensors'                 
    (but not activated)

```

[Wiki]("http://www.lm-sensors.org/wiki/Devices") says they have no plan how to activate it.
```
(2006-09-23) Super I/O with fan monitor. Datasheets available. Often disabled, no plan. 
```

---

