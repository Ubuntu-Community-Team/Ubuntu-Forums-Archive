---
title: "Fan turns on at 41*C. How can I change it?"
date: 2006-04-23
forum: Hardware &amp; Laptops
---

### Post by lmierzej on 2006-04-23
Hi,

is there a configuration file or a script where I can change trip-points for my fan?
My fan turns on at 41*C. Is there any way to change it?

Thanks for Your help,
lmierzej

---

### Post by YuHoo on 2006-04-23
Usually this is not an OS specific thing. Fans are typically controlled by the bios (basic input output system). You can get into it when you first turn on your computer and you have that splash screen. There probably will be a line like "press F2 to enter setup" or something like that. In there you'll find the options to change if they are provided by the manufacturer. But sadly, laptops usually have crappy bioses so they don't offer the options as on a desktop. I hope this solves your problem, and there may be a program to do it from Gnome/KDE/Whatever, but I don't know of any off hand

---

### Post by lmierzej on 2006-04-24
No such opion in bios and I don't think it's not OS specific thing, becouse I can write my own script (using acpi endings, /proc/acpi etc.). It's easy. I just wanted to know, if there is any deamon in ubuntu which takes care about fan speed and where is it's configuration file? ;)

---

### Post by mozetti on 2006-04-24
Last weekend I went through the process of installing and configuring 'fancontrol' and it works pretty well. But, it doesn't allow for inputting temperature triggers. It uses voltage control to adjust the fan speeds (i think, it's Monday ;)  ) and calibrates the fan speeds. But, I think the triggers it uses are automagic.

---

### Post by Egalus on 2006-04-25
[QUOTE=lmierzej]
My fan turns on at 41*C. Is there any way to change it?
[/QUOTE]

Maybe you want to tell us more about the system you are using as fancontrol is hardwaredependent.

---

### Post by lmierzej on 2006-04-26
Maybe you should read my question again. If you know the answer write it please (you do not need to know anything about hardware). If you don't know don't write at all.

---

### Post by kpolice on 2006-04-26
Yes with more information maybe we could help, for example for my Dell I can download i8kutils and control my fans, but it only works with Dell notebooks :P

---

### Post by lmierzej on 2006-04-26
Thank you for your replies.

Something is turning off my fan at 41*C and turning it on at 49*C.

I would like to know where is this magic thing which controls my fan.
Is this a configuration file (maybe somewhere in /etc) or script or a deamon in ubuntu which control it.

I thought that there would be something like powernowd - the deamon which takes care about cpu scaling.

---

### Post by lmierzej on 2006-04-26
I did not install anything for fan control. I have Acer Aspire 1524WMLI.

---

### Post by leche on 2006-04-26
Dude, I don't know if you _should_ be getting any more answers with this attitude... *jeez*

I'll take into account that you are not a native speaker and just consider it a misunderstanding.

for a temporary fix you can change trip points with 
```

echo -n "90:80:55:50:50" > trip_points

```

The numbers being the values at which you want to trip. You can check the current values with
```

cat /proc/acpi/thermal_zone/TZ?/trip_points

```
where TZ? is the thermal zone you are checking (e.g. TZ1).

But what you might wanna consider is installing lm_sensors and changing the conf. accordingly. 

Che

---

### Post by lmierzej on 2006-04-26
Thank you for your answer!

lm_sensors not working - don't support my hardware.
Under /proc/acpi/thermal_zone I have only THRS and THRC - I can only adjust critical temp for shutdown :(

---

