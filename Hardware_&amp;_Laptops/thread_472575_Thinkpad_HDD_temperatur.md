---
title: "Thinkpad HDD temperatur"
date: 2007-06-13
forum: Hardware &amp; Laptops
---

### Post by expoiser on 2007-06-13
Heya

I recently installed Ubuntu on my lenovo thinkpad, I seem to have gotten everything to work, except for some temperature monitoring utility of some sort. I have tryed to install  **Ksensors**
Multiple times, but still no go.. Tells me that there is no sensors detected.

Do any of you have experienced problems with a thinkpad and using this tool. And do you have other suggestions for programs that might give me some of the stats that im looking for?


Thanks in advance
>expoiser<

---

### Post by CrispyFried on 2007-06-13
try acpi -t in a terminal.

---

### Post by infinito on 2007-06-13
You can try [Computer Temperature Monitor]("http://computertemp.berlios.de/") ;)

---

### Post by ramjet_1953 on 2007-06-14
Most new HDD's have SMART so the following should help.

It involves loading two packages from the repositories.

1. [COLOR="Red"]sudo apt-get install hddtemp[/COLOR]

When this installs, it will ask you if you want it to run at system startup, just tick the box and also just use the suggested settings that are displayed.

2.[COLOR="Red"] sudo apt-get install sensors-applet[/COLOR]

You then need to right click on either the top, or bottom bar and select [COLOR="Blue"]add to panel[/COLOR].

Choose [COLOR="Blue"]Hardware Sensors Monitor[/COLOR] from the window list.

Now right click on the new applet and choose [COLOR="Blue"]preferences[/COLOR].

When the window opens, click on the [COLOR="Blue"]Sensors tab[/COLOR].

Click on each sensor and make sure that there is a tick in the box. (sometimes you need to scroll to the right to find the box.

Regards,
Roger :cool:

---

### Post by tgalati4 on 2007-06-14
sudo apt-get install lm-sensors
man sensors
sudo sensors-detect

Edit your /etc/modules list to include the appropriate temperature chip drivers (this is normally done automatically with the sensors-detect script, but it doesn't always work)

sudo sensorsd -s  (to initialize your sensor set, usually only need to do once)
sensors  (to see what sensors you picked up).

Then ksensors will have lots of choices including voltages and fan speeds.

It's late and this is from memory so check for typos if things don't work.

Much more info at lm-sensors.org.  Read and heed.

Good luck.

---

