---
title: "Ubuntu random shutdowns"
date: 2008-08-11
forum: General Help
---

### Post by Jdm111 on 2008-08-11
Im using the laptop and then Ubuntu randomly shuts down!. Sometimes it says critical temperature reached and others it just turns off.
Thanks

---

### Post by Ryadt on 2008-08-11
Can you post the output of```
top
```and ```
acpi -V
```

---

### Post by Jdm111 on 2008-08-11
joe@user-laptop:~$ acpi -V
     Battery 1: charging, 46%, 01:01:57 until charged
     Thermal 1: ok, 57.0 degrees C
  AC Adapter 1: on-line
When i do top i gets longer and longer and i cant copy it.

---

### Post by Dylock on 2008-08-11
Sounds like it's shutting down because your CPU is getting to hot. Has the laptop been cleaned recently? Usually if people use their laptop on carpet it can get pretty nasty in there from all the fibers, or junk in general.

If you think that derby is not the problem then you might want to consider that your fan is going out. One way to check this is to install lm-sensors and monitor the fan rotations.

Another possibility could be your battery. If you have a bad battery they tend to overheat which in term could cause problems for cooling the CPU. Does your battery hold a charge for very long or is it very hot to the touch?

---

### Post by Jdm111 on 2008-08-11
> **Dylock said:**
> Sounds like it's shutting down because your CPU is getting to hot. Has the laptop been cleaned recently? Usually if people use their laptop on carpet it can get pretty nasty in there from all the fibers, or junk in general.

If you think that derby is not the problem then you might want to consider that your fan is going out. One way to check this is to install lm-sensors and monitor the fan rotations.

Another possibility could be your battery. If you have a bad battery they tend to overheat which in term could cause problems for cooling the CPU. Does your battery hold a charge for very long or is it very hot to the touch?

The charge has gone down since i bought it (july 2006). Its warm to touch.

---

### Post by Dylock on 2008-08-11
Well if it's only warm I'd say the battery if probably fine. Usually if a battery is going bad it's to hot to put on your lap.

---

### Post by Jdm111 on 2008-08-11
So what should i do?

---

