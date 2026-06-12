---
title: "CPU Temp App?"
date: 2007-04-30
forum: Hardware &amp; Laptops
---

### Post by craigsharp on 2007-04-30
Hi,  I have E6600 C2D and need to know how hot it's running without restarting and going to my BIOS.  Is there a program that i can install that'll let me know that temp along with other temps?

Thanks

---

### Post by lancest on 2007-04-30
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#General_Notes](http://ubuntuguide.org/wiki/Ubuntu:Feisty#General_Notes)
[COLOR="Blue"]Look for this  How to detect CPU temperature, fan speeds and voltages (lm-sensors)[/COLOR]

Can also use [COLOR="Blue"]acpi -t [/COLOR]at command line.

---

### Post by craigsharp on 2007-04-30
I followed the HOW TO to a "t" and the output is 
```
craig@server:~/Desktop$ sudo sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
```

Not sure where I went wrong.  
I'm runnin an Intel 975 extreme mobo if that matters.

I've heard that the motherboards only work with intels software.

Thanks

---

### Post by lancest on 2007-04-30
Just go to - synaptic package manager and look for **lm-sensors**. You can install it there very easily.  No problem!! Linux handles the quality hardware very well also.

Lance

---

### Post by Syke on 2007-04-30
I like [CompTemp Monitor]("http://computertemp.berlios.de/"). After installing the package, you can then add it to the Gnome panel.

---

### Post by craigsharp on 2007-05-01
I've already installed the X Sensors and nothing showed up in the window.  I downloaded the "computertemp" package and installed, but I dont know where to go to run it.
Thanks
Craig

---

### Post by Syke on 2007-05-01
Click an empty spot up in the bar where you want the little icon to go (like over near the Clock), and select "Add to panel". You'll find an icon for the Computer Temperate in there. Click Add, and you'll get a new icon on your panel that you can then customize by right-clicking on it.

---

### Post by craigsharp on 2007-05-01
When i added it, It does show the icon, but with a big X through it, and says when i hover over it, "No Thermal Monitor Support".

---

### Post by Rui Pais on 2007-05-01
You need first to load the modules for sensors can read from hardware.
run:
```
sudo sensors-detect
```
it will detect the needed one and write the info to /etc/modules automatically. 

hth

---

### Post by craigsharp on 2007-05-01
I had already tried that by following the How To for a previous reply,  But thanks for the help.  It shows NO for all sensors it probes.  I dunno,  I think it's my MOBO.  I've been quite unhappy with it here lately,  I'm thinking about buying a new one.

---

### Post by Rui Pais on 2007-05-01
sorry about that :(

I have a C2C too with a gigabyte intel 945. 
You may try the ones detected for me, sometimes they are very generic and work with a lot of models:
Try:
```
sudo modprobe i2c-i801
sudo modprobe eeprom
sudo modprobe it87
```

and check if sensors work after that. 
If not you can try search for which ones are available inside /lib/modules/<your_kernel_number>/kernel/drivers and load them that way.
It's harmless and you can unload them with modprobe -r <modulename>

good luck.

---

### Post by Atomic Dog on 2007-06-06
> **Syke said:**
> I like [CompTemp Monitor]("http://computertemp.berlios.de/"). After installing the package, you can then add it to the Gnome panel.

I had no joy with lm-sensors following the instructions on that wiki.  But CompTemp Monitor did install and work for the CPU (I;m assuming it's reading the cpu sensor).  I know there is more than one sensor in this new laptop, but I'll take just cpu.  I'd love to monitor the HD and case too.

---

### Post by Syke on 2007-06-06
Right-click the icon and select Preferences. You should be able to switch the sensor to HDDTEMP.

---

### Post by Atomic Dog on 2007-06-06
> **Syke said:**
> Right-click the icon and select Preferences. You should be able to switch the sensor to HDDTEMP.

Yea.  Tried that.  Only ACPI gives one thermal zone to choose.  If I select "kernel i2c sensors" then I have no thermal zones.  Kind of a bummer.

---

