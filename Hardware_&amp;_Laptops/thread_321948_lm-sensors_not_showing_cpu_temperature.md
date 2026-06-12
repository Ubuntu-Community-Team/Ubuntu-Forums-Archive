---
title: "lm-sensors not showing cpu temperature"
date: 2006-12-19
forum: Hardware &amp; Laptops
---

### Post by belda on 2006-12-19
i got a little problem
i've allready convinced my new asus p5b-e with core 2 duo to work well and installed lm-sensors on it. but i can just get it to show voltages and mb temperature. but i cant get it to show the cpu temp nor it shows the cpu fan speed

i got
2.6.17.13 kernel with nvidia 9631
lm sensors 1:2.10.0-7ubuntu3

---

### Post by robenroute on 2006-12-30
Have a look at [Phoronix]("http://www.phoronix.com"), they regularly test motherboards and most of the motherboards they test show limitations as far as full Linux support goes (including lm-sensors). Sometimes the temp sensor works, sometimes the fan speed sensors work, sometimes nothing works, sometimes most things work. It's a bit of a hit-and-miss situation.

They (Phoronix) recently tested the Abit KN9 Ultra (which is an AMD dual-core board (AM2 socket)), and they were very positive about this board. It proves to be one of the best "Linux" boards out there.

I'm about to build a new PC myself and just for this very reason, I'm seriously pondering to go the AMD route. What good is an all-singing, all-dancing C2D board (or AM2, or any other board, for that matter) if the support under Linux is shoddy? Sure, Intels Core 2 Duos seem to be the better processor these days, but honestly, would you notice the difference in performance between a C2D and an X2 (similar specs)? I'd rather have a motherboard (and other components, of course) that functions smoothly and properly with my chosen OS (Linux in this case) than have the fanciest hardware, but it isn't supported properly/fully. If the penalty for that is waiting 1 second longer for OpenOffice to open, or having to stare at the screen 2 milliseconds longer, waiting for the file copy to finish, so be it!

Just my very humble opinion....

P.S. On top of all of this, a KN9 Ultra can be bought for less than $100 (about 85 euros), add a very capable X2-3800 (or 4200) and you're A-for-away for less than $250.

---

### Post by miceagol on 2007-01-13
> **belda said:**
> i got a little problem
i've allready convinced my new asus p5b-e with core 2 duo to work well and installed lm-sensors on it. but i can just get it to show voltages and mb temperature. but i cant get it to show the cpu temp nor it shows the cpu fan speed


I've got this mobo myself, but I'm not sure what lm-sensors show me: 
```

michaeka@thedarkside:~$ sensors
lm78-isa-0290
Adapter: ISA adapter
VCore 1:   +2.26 V  (min =  +0.00 V, max =  +3.49 V)   
VCore 2:   +3.76 V  (min =  +2.18 V, max =  +0.06 V)   
+3.3V:     +3.26 V  (min =  +0.00 V, max =  +0.00 V)   
+5V:       +5.48 V  (min =  +0.00 V, max =  +0.22 V)   
+12V:      +7.11 V  (min =  +0.06 V, max =  +0.43 V)   
-12V:     -11.13 V  (min =  -0.00 V, max =  -0.45 V)   
-5V:       -2.77 V  (min =  -0.39 V, max =  -3.08 V)   
fan1:        0 RPM  (min = 75000 RPM, div = 2)          
fan2:     2678 RPM  (min = 168750 RPM, div = 4)          
fan3:        0 RPM  (min = 3013 RPM, div = 2)          
temp:      +42.0°C  (high =    +0°C, hyst =    +0°C)   
vid:       +3.00 V

```

I know that fan2 is my cpu fan, as 2600 RPM is approximately its speed (my two case fans move at 1000 RPM). But "temp" might be both mobo and cpu, but I think its mobo. Anybody with P5B-E know if its possible to get CPU temp and case fan speeds information?

---

### Post by Orfeous on 2007-07-08
i cant get any information from lm-sensors from my p5b deluxe vista... i have tried many things with no success

---

### Post by jolly79 on 2007-08-29
Hi

when i type: sensors i my terminal i get this response:

jolly79@jolly79-desktop:~$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
             +23°C
Core1 Temp:
             +29°C


Is this the real temp of my CPU??, i know it´s a little of topic.
I run at Asus a2m-delux bord.

Hope you can answer my question, because i would love to be able toe read my Cpu temp :-)

---

### Post by ramjet_1953 on 2007-08-29
Some motherboards don't like lm-sensors.

Try a different approach.

[COLOR="Red"]sudo apt-get install sensors-applet[/COLOR]

Now, right-click on a blank space in either the top, or bottom task bar and select [COLOR="Blue"]Add to Panel[/COLOR],

When the window opens, scroll down to [COLOR="Blue"]System and Hardware[/COLOR]

Select [COLOR="Blue"]Hardware Sensors Monitor[/COLOR]

Click on the [COLOR="Blue"]Add Button.[/COLOR]

A CPU Temperature Sensor should now appear in the task bar.

If you want to also add monitoring for your hard drive do this:

[COLOR="Red"]sudo apt-get install hddtemp[/COLOR]

It will ask you a couple of questions about auto starting the daemon and which port to monitor. Just choose the defaults.

Now, right click on the CPU icon that you previously installed.

Click on[COLOR="Blue"] Preferences.[/COLOR]

Click on the [COLOR="Blue"]Sensors Tab[/COLOR]

Click on the [COLOR="Blue"]hdtemp item[/COLOR] and when the tree opens, make sure that there is a tick in the box next to the hddtemp listing.

Regards,
Roger 8)

---

### Post by andoty_jazz on 2007-08-31
**Works like a charm!**

Installed gdesklets but got no luck on it.

Thanks for this tip and guided tut.

Long live Ubuntu.

---

