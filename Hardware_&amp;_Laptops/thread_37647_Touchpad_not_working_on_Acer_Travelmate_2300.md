---
title: "Touchpad not working on Acer Travelmate 2300"
date: 2005-05-28
forum: Hardware &amp; Laptops
---

### Post by ssck on 2005-05-28
Hi ALL,

Does anybody know how to get the touchpad to work on Acer Travelmate 2300 ? Would appreciate any help.

Thanks.

---

### Post by ::DoGG:: on 2005-05-28
Do You know what kind of touchpad is it ? Alps, Synaptics ??
basically try to boot and when x server starts open terminal and type:
```
rmmod tsdev
rmmod evdev
rmmod psmouse
modprobe tsdev
modprobe evdev
modprobe psmouse
```

and see if now the touchpad is working.

---

### Post by ssck on 2005-05-29
[QUOTE=::DoGG::]Do You know what kind of touchpad is it ? Alps, Synaptics ??
basically try to boot and when x server starts open terminal and type:
```
rmmod tsdev
rmmod evdev
rmmod psmouse
modprobe tsdev
modprobe evdev
modprobe psmouse
```

and see if now the touchpad is working.[/QUOTE]


it is a synaptics touchpad.what do i need to do ? do i issue the commands stated ?

thanks

---

### Post by ::DoGG:: on 2005-05-29
yeah, just do the code that o got you above, works on mine machine, i don`t know why but after bootup i had to reload these modules by hand to get touchpad working, since it`s synaptics you shouldn`t have much problem.

---

### Post by ssck on 2005-05-29
[QUOTE=::DoGG::]yeah, just do the code that o got you above, works on mine machine, i don`t know why but after bootup i had to reload these modules by hand to get touchpad working, since it`s synaptics you shouldn`t have much problem.[/QUOTE]

managed to rmmod both except evdev.the message was 'device is in use'

i then modproble all three but there was no response when i used the touchpad.i remember distinctly that when ubuntu was first installed (or when i was running the live cd), it was working perfectly.

what else can i do ?

thanks for your help.

---

