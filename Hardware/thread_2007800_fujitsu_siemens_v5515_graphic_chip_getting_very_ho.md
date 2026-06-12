---
title: "fujitsu siemens v5515 graphic chip getting very hot."
date: 2012-06-21
forum: Hardware
---

### Post by noxified on 2012-06-21
i've got a question about those laptops with this graphic card.
i've got a _fujitsu siemens v5515_ (sis mirage m671) and his grapich chip is getting very hot.processor is on 45 degrees,and hdd ,same. But palmrest,and touchpad are getting very hot.I cleaned it up,changed thermal paste (with arctic silver 5) ,on cpu ,and graphical chip too,and no results on getting hot.i tryed coodpad,but i don't really like it,and don't really do the trick(is's that kind that you can move fans where you want,and i put them right beside processor and graphical chip) (with the case open).i tryed putting a 1mm cooper pad between graphic chip and the radiator,with thermal paste between.. nothing worked..how can i fix it?
it's that normal?
how can i fix it?

---

### Post by noxified on 2012-06-22
bump

---

### Post by Redblade20XX on 2012-06-22
Try looking into cpu scaling. Maybe the system is setup to run the cpu at max speed even when there is little work which causes immense power usage and thermal buildup.

Take a look at the jupiter project: [http://www.ubuntugeek.com/tag/install-jupiter-ubuntu-12-04](http://www.ubuntugeek.com/tag/install-jupiter-ubuntu-12-04)

Also what graphics card do you have? Do you have the opensource drivers installed or the proprietary ones installed? Usually the proprietary ones have better thermal controls.

-Red

---

### Post by noxified on 2012-06-23
i tryed that applet already.there's no difference.
and about the graphic card(there is the problem) there's no proprietary drivers,only vesa drivers...
cpu temperature is pretty low,i'm pretty sure that dosn't the problem..

---

### Post by noxified on 2012-06-24
bump

---

### Post by noxified on 2012-06-25
bump

---

### Post by noxified on 2012-06-27
bump

---

### Post by na5h on 2012-06-27
This isn't exactly my area of expertise, but AFAIK, +45 (celsius) degrees is not very hot for a CPU. Critical temp. is usually around +100 degrees.

What is your output of the following command?
```
sensors
``` 

You might have to install the sensors first by typing:
```
sudo apt-get install lm-sensors
```

---

### Post by noxified on 2012-06-27
not cpu temperature i'm worried about
i'm worried about graphic chip.that chip get VERY HOT.
there's no sensor on it,so i don't know temperaure around there,but if i touch it with the finger it feels way hotter than the cpu.
the palmrest and the touchpad are feeling very hot also....

---

### Post by na5h on 2012-06-28
It's quite common for the chassis to get hot, it doesn't necessarily mean that the laptop is overheating.

What is your output of the following command (look for the line that says "VGA compatible controller")?
```
lspci
```

Are you absolutely certain that the "sensors" command doesn't give you the temperature of the GPU? You should at least try it just to make sure...

---

