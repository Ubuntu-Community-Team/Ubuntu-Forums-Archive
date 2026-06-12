---
title: "Laptop fan Does not work when under ubuntu."
date: 2009-05-13
forum: Hardware
---

### Post by villevalorox on 2009-05-13
OK, I just noticed my laptop fan does not run while I'm in ubuntu (works fine under xp) But I went to pick my laptop up and it burnt my hand. It was really really hot. I look around and noticed that the fan was not running and should have been considering how hot my computer was. I booted up in xp and as soon as I did the fan kicked on high. Is this an incompatible issue with hardware? How can I fix this? thanks. 

I'm on a toshiba a1005 , also if anyone can help the brightenss does not work under Ubuntu at all. and it drains my comp dead super fast when on the battery. thanks :)

---

### Post by doas777 on 2009-05-13
I cant help with the fan (though i'd like to know how to), but you may be able to monitor your temp with lm-sensors and sensors-applet(a gnome panel applet that displays lm-sensors output)

just 
```

sudo apt-get install lm-sensors sensors-applet
sudo sensors-detect


``` 
say yes to all the questions sensors-detect asks, 
and then add (to a gnome panel) the Hardware Sensor Monitors applet.
you may need to reboot before some sensor values.
if you get duplicates (many mobos have multiple sensors) take the most reasonable ones, and uncheck the others in your preferences.

good luck

---

### Post by villevalorox on 2009-05-13
Thanks :) ... so if any of them are red should I stop ubuntu and let my system cool down?

---

### Post by doas777 on 2009-05-14
well, you have to calibrate the color codes to your hardware. my CPU is rated to handle up to 90-100 deg Celcius, but older ones are usually in danger at 70-75 C. 
Smooth operation for my laptop CPU is between 30 and 60C and when the CPU hits 75 or so (which is very rare) I hear the fan start up and I usually shut down then.

your GPU is a little different, it will most likly always idle between 55 and 65, and get up to 90 under a load (like a game or whatever).

Hard disks are sometimes less tolerant of heat, so you may want to look up the max thermal for your hdd model to determine what is the safe level.

I got one of those laptop cooling plates (a full sized 17" one for my 17" laptop) and it dropped my temperature by at least 20 degrees C, and I am no longer worried if I happen to leave it on overnight or somthing.

good luck

---

