---
title: "MAC Address log"
date: 2014-07-18
forum: Hardware
---

### Post by vni.jamie on 2014-07-18
I'm not certain what category this question falls under.

Is there any standard location I could find a log of MAC addresses that have previously been connected to Ubuntu14?

I'm working on a TM4C129X LaunchPad that locked up and I ended up re-flashing it. Unfortunately this killed it's original MAC address and I didn't have the foresight to write down the original.

I was hoping that there might be a log file kicking around somewhere with a record of the address from when I previously connected the device.

---

### Post by varunendra on 2014-07-19
Welcome to the forums vni.jamie !

Assuming it is detected as a network card by the system, take a look at udev rules file that contains information about such devices including their mac addresses -
```
cat /etc/udev/rules.d/70-persistent-net.rules
```

---

