---
title: "CPU Temperature"
date: 2008-08-13
forum: General Help
---

### Post by PCessna on 2008-08-13
Hello all,

Does anyone know a CPU temperature and such applet that I can put on my top menu :)

Thanks
-PCessna **_(Ubuntu 8.04 LTS hardy 64-bit)_**

---

### Post by tuxxy on 2008-08-13
YOu can easily include CPU temps in conky if you have it installed

---

### Post by tamoneya on 2008-08-13
> **PCessna said:**
> Hello all,

Does anyone know a CPU temperature and such applet that I can put on my top menu :)

Thanks
-PCessna **_(Ubuntu 8.04 LTS hardy 64-bit)_**

temperatures are best measured with lm-sensors.  I do also recommend conky though but it is just the front end of lm-sensors.

---

### Post by PCessna on 2008-08-13
> **tamoneya said:**
> temperatures are best measured with lm-sensors.  I do also recommend conky though but it is just the front end of lm-sensors.

when installing conky, rebooting, and logging out, I cannot use conky.

---

### Post by PCessna on 2008-08-13
> **PCessna said:**
> when installing conky, rebooting, and logging out, I cannot use conky.

:confused:

---

### Post by tamoneya on 2008-08-13
can you post your conkyrc file.  Also did you install lm-sensors yet?  If not look here: [http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

If you install just conky and no lmsensors you will only be able to see things like CPU usage, RAM usage. No temps or fan speeds.

---

### Post by PCessna on 2008-08-13
> **tamoneya said:**
> can you post your conkyrc file.  Also did you install lm-sensors yet?  If not look here: [http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

If you install just conky and no lmsensors you will only be able to see things like CPU usage, RAM usage. No temps or fan speeds.

way too confusing, ill just wait for my mac to see that kinda stuff

---

### Post by PCessna on 2008-08-14
bump

---

### Post by kerry_s on 2008-08-14
i just made my own to check on the temp from time to time, i just oc'd from 1.5 to 1.7ghz and want to make sure it stays cool enough.

the script i used:
```
#!/bin/sh
cat /proc/acpi/thermal_zone/THRM/temperature > ~/.cpu-temp
xmessage -center -file ~/.cpu-temp
```

pic of launcher:

---

### Post by dje on 2008-08-14
in terminal:
```
sudo apt-get install sensors-applet
```
right click on panel >> add to panel >> hardware sensors monitor

dje

---

### Post by kerry_s on 2008-08-14
> **dje said:**
> in terminal:
```
sudo apt-get install sensors-applet
```
right click on panel >> add to panel >> hardware sensors monitor

dje

that works for me, but you have to log out and back in after you install it to see it.

i was surprised it's not using much resources. :)

---

### Post by PCessna on 2008-08-14
Gah, I only see GPU, I Need help, I wanted CPU D:

---

### Post by kerry_s on 2008-08-14
> **PCessna said:**
> Gah, I only see GPU, I Need help, I wanted CPU D:

right click the applet> preferences> sensors
see if you have it there but not activated.

mine looks like this:

---

### Post by PCessna on 2008-08-15
> **kerry_s said:**
> right click the applet> preferences> sensors
see if you have it there but not activated.

mine looks like this:

Ok. AHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHh. I'm good, I already checked this. ONLY GPU is there, which is 180oF which is bullcrap, if it was that hot my comp wouldn't sound so normal. Can someone please help me ?

---

### Post by PCessna on 2008-08-15
> **PCessna said:**
> Ok. AHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHh. I'm good, I already checked this. ONLY GPU is there, which is 180oF which is bullcrap, if it was that hot my comp wouldn't sound so normal. Can someone please help me ?

help please

---

### Post by dje on 2008-08-15
> **PCessna said:**
> help please

see if [this page]("http://www.compdigitec.com/labs/2008/07/18/measure-cpu-temp-in-ubuntu/") helps

dje

---

### Post by PCessna on 2008-08-15
> **dje said:**
> see if [this page]("http://www.compdigitec.com/labs/2008/07/18/measure-cpu-temp-in-ubuntu/") helps

dje
This made me feel helpless and did nothing, thanks for trying though :(

---

### Post by PCessna on 2008-08-16
> **PCessna said:**
> This made me feel helpless and did nothing, thanks for trying though :(

bump

---

### Post by quazi on 2008-08-16
> **PCessna said:**
> Ok. AHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHh. I'm good, I already checked this. ONLY GPU is there, which is 180oF which is bullcrap, if it was that hot my comp wouldn't sound so normal. Can someone please help me ?

I'm not sure if this helps, but 180 degrees F is "only" 83 degrees Celsius.  While that's hardly an optimal temperature, it's definitely believable.

---

### Post by fcorourke on 2009-02-19
Hi all, the install that dje posted worked perfect on my Dual Core, both came up    no problem. I did see 82 C. on my computer the other day with the AC off & me gone. That was from bios after it craassshed as I walked in :-) now running about 60 & 50 -- OK as I am building a new system in a week or two all parts in.

---

