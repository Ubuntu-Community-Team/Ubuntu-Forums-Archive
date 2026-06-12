---
title: "Home automation / HVAC control"
date: 2011-05-23
forum: Hardware
---

### Post by MP002 on 2011-05-23
Hi,

I'm looking for a solution for controlling **air conditioners** to run on a **headless** ubuntu server.

Hardware should be USB only.
It should receive and send infrared but also learn from signal of any original remote.
Software should support multiple hardware modules (air conditioners are on multiple storeys, are of the same model but need different settings)
Software should be command line (scripts) only, no GUI.
Also looking for temperature and hygro sensors, also USB.

The electronics box can be located near the server, but sensors and receiving/transmitting diodes should support cables up to 30 metres in length.

I'm from Europe.
If anyone has some experiences and suggestions or can point me to the right direction, I'll be most grateful.

---

### Post by dargaud on 2011-05-23
USB doesn't go farther than 1.5 meters, that's why home automation uses just about any other connectivity _but_ USB: serial, ethernet, RS485 and plenty of dedicated things.

---

### Post by MP002 on 2011-05-23
I know. I would not want that even if was possible.
I need only sensors that far, not the hardware device.

---

