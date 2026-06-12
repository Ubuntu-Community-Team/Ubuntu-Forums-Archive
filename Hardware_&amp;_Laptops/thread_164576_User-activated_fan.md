---
title: "User-activated fan?"
date: 2006-04-23
forum: Hardware &amp; Laptops
---

### Post by Narpas on 2006-04-23
My laptop - Dell Inspiron 1200 - apparently likes to run hot. It'll happily get up to 60 Degrees C before kicking on the fan - not great for the computer, really not great for my legs. I'd like something where I could activate the fan at will. Not override the automatic capibilities, of course, but if the automatic system doesn't want to work, I want to have a manual override. Any ideas? I use GKrellM with a Dell temp/fan plugin, but I don't think lowering the values in that actually changes when the fan activates.

---

### Post by nanotube on 2006-04-23
if you install i8kutils package (i think that's its name... just search in synaptic for i8k), it will come with some utilities for dell. one of them is i8kfan, which will allow you to turn on/off the fan. you can even set that stuff up to run in daemon mode, and automatically kick in at whatever temperature you set.

---

### Post by paritybit on 2006-04-23
[QUOTE=nanotube]if you install i8kutils package (i think that's its name... just search in synaptic for i8k), it will come with some utilities for dell. one of them is i8kfan, which will allow you to turn on/off the fan. you can even set that stuff up to run in daemon mode, and automatically kick in at whatever temperature you set.[/QUOTE]
You will also need to do a 
```
sudo modprobe i8k
```
so install the module for the fan control.

---

### Post by paritybit on 2006-04-23
as a side note.. does this disable the acpi fan control?
I turned the fan off and started a kernel compile to kill the cpu. I turned the fan back on at 80C, I chickened out.
There doesn't seem to be an option that sets things back to default. Any clues?

---

### Post by nanotube on 2006-04-23
hey
btw, you can check out the link in my sig, and go to the temperature and fan sensors section for more details on how to install the i8k stuff.

also, afaik, the fan control is "normally" done by the bios, but i may be wrong...

---

### Post by Narpas on 2006-04-23
Thanks a ton. I've got one last question: How do I put the fans on automatic controll again after putting "i8kfan 1 1" (or somesuch) into my terminal? My lappy is now at a cozy 35*C, and I think it could stay that way.

GKrellm doesn't seem to have any controll over my fans.

Ooh. As I was writing this post, I thought of a way, and it works. In the sensor applet (see nanotube's link) I just set an alarm with the command to activate the fan. The fan stays on untill I manually turn it off.

---

### Post by paritybit on 2006-04-23
I saw that but doesn't appear there are multiple ones, so say at 40C you can use i8kfan 1 1 and then at 60C user i8kfan 2 2.
and then of course back down. As far as I can tell these events will just set your fan to a speed and it will stay there....

---

### Post by nanotube on 2006-04-23
[QUOTE=paritybit]I saw that but doesn't appear there are multiple ones, so say at 40C you can use i8kfan 1 1 and then at 60C user i8kfan 2 2.
and then of course back down. As far as I can tell these events will just set your fan to a speed and it will stay there....[/QUOTE]

to do this, you need to use i8kmon in daemon mode.
```
man i8kmon
```
for more detail. :)

---

