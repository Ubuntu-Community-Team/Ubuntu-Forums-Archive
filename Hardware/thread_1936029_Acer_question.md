---
title: "Acer question"
date: 2012-03-05
forum: Hardware
---

### Post by Tiganjero on 2012-03-05
Does anyone happen to know which files represent the state of LEDs on an Acer laptop (5920G in my case). I use this machine as a portable server, and have already wrote a script that alerts me using festival when battery charge drops below 10% and it'd be nice to add some flickering lights too.

Cheers,
George

---

### Post by Tiganjero on 2012-03-05
Found 'em. The file that defines the state of the WLAN LED is *[SIZE="1"]/sys/devices/platform/acer-wmi/rfkill/rfkill1/state[/SIZE]* and the same file for the bluetooth LED is *[SIZE="1"]/sys/devices/platform/acer-wmi/rfkill/rfkill2/state[/SIZE]*. I'm not sure whether the power and battery LEDs can be turned on and off, but I think they can't.

Cheers,
George

---

