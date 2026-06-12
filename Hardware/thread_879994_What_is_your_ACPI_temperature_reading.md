---
title: "What is your ACPI temperature reading?"
date: 2008-08-04
forum: Hardware
---

### Post by kaoskorruption on 2008-08-04
Just of of curiosity, what is your acpi temperature? Mine is averaging between 40 and 50 C. No idea if that is good or bad. 

[Gateway T-6836]

---

### Post by robenroute on 2008-08-04
Same here (on an HP 6710b laptop): CPU reads about 50 deg. C, board (or is it the case?) between 45 and 60 deg.

---

### Post by yojimba on 2008-08-05
As a Linux newb . . . what is the command used to check case and cpu temps? Is there a program I can run that will monitor temps? Thanks.

---

### Post by Nicu Alecu on 2008-08-05
In terminal, just type:
[INDENT]acpi -t[/INDENT]
and hit enter.

---

### Post by yojimba on 2008-08-09
thanks. i'm working on a fanless system and am looking for a package that will monitor and log temperatures (CPU and MB) over an extended time period. any suggestions?

---

### Post by istblacken on 2008-08-09
you can use the applets from gnome panel. right click panel and choose add.

---

### Post by TenPlus1 on 2008-08-09
47 o C

---

### Post by gila_monster on 2008-08-09
My Gateway 4525GZ runs typically between 40 and 50C. Fan kicks on around 43C. I'd say your temps are pretty typical.

---

### Post by Vishal Agarwal on 2008-08-09
The Total Output of acpi -t -V command is :

Battery 1: charged, 100%
Thermal 1: ok, 52.0 degrees C
AC Adapter 1: on-line

---

### Post by sdennie on 2008-08-09
```

$ acpi -t
     Battery 1: discharging, 51%, 02:58:22 remaining
     Thermal 1: ok, 33.0 degrees C

```

On a laptop, cleaning out the all the vents at least once a month with compressed air makes a huge difference in heat.  Also, enabling various power savings features cools the machine a great deal.

---

### Post by benerivo on 2008-08-09
Thermal 1: ok, 10.0 degrees C

---

### Post by mcduck on 2008-08-09
58°C. With a Core Duo T2300 on a laptop. The fan won't really even start spinning until around 65°C.. ;)

It would probably be a good idea to mention the CPU model as well, as there is no default for a correct temperature for _all_ CPU's, the thermal design powers of different processors vary between 2W and 165W, and thus the max temperatures can be very different on different hardware.. Not to mention the effect of different types of cooling..

edit: benerivo: either you are using a compressor/liquid CO2/LN2 cooling, or you are running the machine in sub-zero temps, or that reading is ridiculously incorrect.. :D

---

### Post by damis648 on 2008-08-09
Intel T9300: Both cores at 52C typing this message.
Nvidia 8600M GT GPU: 62C with Compiz.

---

### Post by jerome1232 on 2008-08-09
AMD 64 3700+ : 30 c  (not sure if this is correct I do have fan intended for a much higher clocked processor though)

---

### Post by Kevbert on 2008-08-09
> **yojimba said:**
> thanks. i'm working on a fanless system and am looking for a package that will monitor and log temperatures (CPU and MB) over an extended time period. any suggestions?

You want to take a look at the [[COLOR="Red"]conky post[/COLOR]]("http://ubuntuforums.org/showthread.php?t=281865&highlight=conky&page=322") #3219 onwards.

---

### Post by sdennie on 2008-08-09
> **mcduck said:**
> 
It would probably be a good idea to mention the CPU model as well, as there is no default for a correct temperature for _all_ CPU's


Agreed.  My 33C was from a laptop with a T9300 CPU.  It also has an nvidia 8400M GS which is at 46C at the moment.  Admittedly, it's winter here and the ambient temperature is quite low to begin with but, the CPU temperature generally fluctuates between 30C and 42C (at which point the fan kicks on).

> 
edit: benerivo: either you are using a compressor/liquid CO2/LN2 cooling, or you are running the machine in sub-zero temps, or that reading is ridiculously incorrect.. :D

Haha.  10C is quite cool...

---

### Post by benerivo on 2008-08-09
> edit: benerivo: either you are using a compressor/liquid CO2/LN2 cooling, or you are running the machine in sub-zero temps, or that reading is ridiculously incorrect

Your not kidding! I'm sure it's giving me a false reading but i've no idea why. I'll reboot and enter the bios to tell you the real figure soon...

EDIT - From the BIOS, my P4 desktop machine's CPU is at 40C, not 10C as acpi -t reports.

---

### Post by Kevbert on 2008-08-10
> **benerivo said:**
> Your not kidding! I'm sure it's giving me a false reading but i've no idea why. I'll reboot and enter the bios to tell you the real figure soon...

EDIT - From the BIOS, my P4 desktop machine's CPU is at 40C, not 10C as acpi -t reports.

It might be worth raising a bug report in [[COLOR="Red"]Launchpad[/COLOR]]("https://bugs.launchpad.net/").

---

### Post by yojimba on 2008-08-11
> **Kevbert said:**
> You want to take a look at the [[COLOR="Red"]conky post[/COLOR]]("http://ubuntuforums.org/showthread.php?t=281865&highlight=conky&page=322") #3219 onwards.

Great link thanks . . . definitely going to give Conky a look along with Computer Temperature monitor . . .

I've been running Mythbuntu and have realized that if I want to do much of anything outside of MythTV (e.g., temp monitoring, bluetooth, applet support)it is much better to do a full Ubuntu and run Myth with Ubuntu . . . 

Mythbuntu is great but it leaves most everything out that doesn't relate directly to MythTV . . .

I couldn't figure out why I was having such difficulty running simple commands such as acpi -t or sensors . . . and why I couldn't load or find any applets on the task bar . . . :guitar:

---

### Post by Bruce M. on 2008-08-15
```
bruloo@bruloo:~$ acpi -t
     Thermal 1: ok, 22.0 degrees C

```

---

### Post by 5nak3 on 2009-01-11
Well my ACPI ranges from 40-50 usually, the thing is i'm pretty sure that is not the actually temperature of the components.

When i was running XP i used a utility called Mobile Meter (google Mobmeter)
That was showing me a temp of 60 so I cleaned out the fans saw a huge drop to 30, since then, i've cleaned the fans every so often. Mob meter seemed to actually measure either the Mother Board or CPU, can't remember which, and actually I can't remember if it stated which. I know for sure it measured HDD temp, CPU speed.

In any case with Ubuntu, lm_sensors does not seem to pick up either processor or mother board, and so I'm using ACPI Therm measures.
I felt that the 40-50 was a high reading from the ACPI compared to the 30 i was getting with XP and Mob Meter, so I bought a cooling pad for the laptop hoping to see if things change.

Even with the cooling pad i still get readings in the 40's and 50's (even on boot). The laptop feels cooler to the touch so I'm guessing the reading is wrong.

For instance 20min in Openarena, the laptop feels much warmer ACPI reads 57 degrees.

20min sitting idle playing some music, the laptop feels cooler but ACPI reads 54...

I'm not sure what ACPI actually measures, but it does not seem to be correct. I'm charging the battery now, I might remove that later on and see what the ACPI reads, because I have a feeling the more current being drained the higher the ACPI.

In fact I saw the ACPI exceed 80 degrees, while I was burning a backup of my documents plus surfing the web. 

If anyone has any other programs or methods of reading the temperature I would sure like to know so as to justify the cooling pad purchase ;)

If it is of any interest the laptop i'm using is a Compaq R3000 terrible cooling, they stuck a P4 3.2ghz processor in the laptop and only gave it small vents...funny thing is the fans on this one are on all the time, it could be idle, it could be burning a CD doesn't matter the fans keep on spinning.

---

### Post by mrowth on 2009-01-11
> **Nicu Alecu said:**
> In terminal, just type:
[INDENT]acpi -t[/INDENT]
and hit enter.
No support for device type: thermal

Also, I don't know how to control either the CPU frequency or the fan speed or both. Everything's going at full speed (& volume); fortunately, this isn't a laptop.

I can get Core 1, Core 2 and GPU temperature readings through Conky or GKrellm, though. 40-41°C, 35-37°C, 40-41°C right now. Running Compiz and the usual bunch of non-multimedial Internet apps.

AMD 64 X2 4800+, Geforce 7950 GT, ASUS A8V board. It has "ASUS Q-Fan 2 Technology" and "ASUS Cool 'n' Quiet! (tm) Technology", whatever those are.

---

### Post by HDTimeshifter on 2009-01-11
> **Nicu Alecu said:**
> In terminal, just type:
[INDENT]acpi -t[/INDENT]
and hit enter.

I get nothing:

:~$ acpi -t
:~$ acpi
:~$ acpi -t -V
     Cooling 0: Processor 0 of 3
     Cooling 1: Processor 0 of 3
     Cooling 2: Processor 0 of 3
     Cooling 3: Processor 0 of 3

I thought I have ACPI enabled, but will check the BIOS next time I reboot.

---

### Post by 5nak3 on 2009-01-11
could someone please just tell me what the ACPI is actually measuring?

---

### Post by AKADAP on 2009-01-11
intel i7 920 on an Asus P6T Delux mother board:

acpi -t
(nothing)
acpi -V
```
     Cooling 0: Processor 0 of 3
     Cooling 1: Processor 0 of 3
     Cooling 2: Processor 0 of 3
     Cooling 3: Processor 0 of 3
     Cooling 4: Processor 0 of 3
     Cooling 5: Processor 0 of 3
     Cooling 6: Processor 0 of 3
     Cooling 7: Processor 0 of 3

```
I don't think my mother board is supported yet.

---

### Post by JohnoDC on 2009-01-11
acpi -t -V
     Battery 0: Full, 100%
  AC Adapter 0: on-line
     Thermal 0: ok, 52.0 degrees C
     Thermal 1: ok, 52.0 degrees C
     Cooling 0: Processor 0 of 10
     Cooling 1: Processor 0 of 10

Intel(R) Core(TM)2 CPU T5500 @ 1.66GHz

This is on an Acer Aspire 5630 laptop, Haven't got Ubuntu installed on my desktop yet.

---

### Post by HDTimeshifter on 2009-01-11
> **JohnoDC said:**
> acpi -t -V
     Battery 0: Full, 100%
  AC Adapter 0: on-line
     Thermal 0: ok, 52.0 degrees C
     Thermal 1: ok, 52.0 degrees C
     Cooling 0: Processor 0 of 10
     Cooling 1: Processor 0 of 10

Intel(R) Core(TM)2 CPU T5500 @ 1.66GHz

This is on an Acer Aspire 5630 laptop, Haven't got Ubuntu installed on my desktop yet.

I have the same laptop.  Nice to know Ubuntu runs on it, should I ever decide to wipe out my only Vista PC.

---

### Post by 00b00nt00 on 2009-01-11
Mobile Pentium III @ 800 Mhz. 60 degrees C while playing Flash video.

---

### Post by sofasurfer on 2009-01-23
~$ acpi -t -V
     Thermal 0: ok, 40.0 degrees C
     Cooling 0: Processor 0 of 3
     Cooling 1: Fan 1 of 1

---

### Post by Sorivenul on 2009-01-23
> 
     Battery 0: Charging, 100%
  AC Adapter 0: on-line
     Thermal 0: ok, 52.0 degrees C

BASIC SPECS:
Sony VAIO VGN-FS980, 1.73GHz Centrino, 1GB RAM

CURRENT TASKS:
Browsing Ubuntu Forums, compiling a "[buildroot]("http://buildroot.uclibc.org/")" system, IRC chat.

---

### Post by jfr1tz on 2009-01-24
> coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +28.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +30.0°C  (high = +100.0°C, crit = +100.0°C)  


just browsing, c2d throtthled back to 800Mhz, it maxes out at 61C under very heavy load(multiple VM's)

SL300.

---

### Post by HDTimeshifter on 2009-02-06
> **AKADAP said:**
> intel i7 920 on an Asus P6T Delux mother board:

acpi -t
(nothing)
acpi -V
```
     Cooling 0: Processor 0 of 3
     Cooling 1: Processor 0 of 3
     Cooling 2: Processor 0 of 3
     Cooling 3: Processor 0 of 3
     Cooling 4: Processor 0 of 3
     Cooling 5: Processor 0 of 3
     Cooling 6: Processor 0 of 3
     Cooling 7: Processor 0 of 3

```
I don't think my mother board is supported yet.

I turned on ACPI at last reboot, but I still get nothing like above.  I find it hard to believe my MB isn't supported either, since I bought it back in October.  ASUS P5Q Pro

---

### Post by boblizar on 2009-02-18
what is the name of the package that has the acpi -t command?

i have lm_sensors working, but have a conkyrc that uses acpi commands and would like to get acpi working also.

this is for a phenom am2+ 9950 quad core with 8gb of ram.  im asking the package name since im a linux from scratch person =)

```
mkultra [ ~/Desktop/ospmd-20021122/ospmd ]$ sensors
it8718-isa-0228
Adapter: ISA adapter
in0:         +1.28 V  (min =  +0.00 V, max =  +4.08 V)
in1:         +1.90 V  (min =  +0.00 V, max =  +4.08 V)
in2:         +3.34 V  (min =  +0.00 V, max =  +4.08 V)
in3:         +3.01 V  (min =  +0.00 V, max =  +4.08 V)
in4:         +3.07 V  (min =  +0.00 V, max =  +4.08 V)
in5:         +3.22 V  (min =  +0.00 V, max =  +4.08 V)
in6:         +4.08 V  (min =  +0.00 V, max =  +4.08 V)
in7:         +0.24 V  (min =  +0.00 V, max =  +4.08 V)
in8:         +3.07 V
fan1:       3260 RPM  (min =    0 RPM)
fan2:          0 RPM  (min =    0 RPM)
fan3:          0 RPM  (min =    0 RPM)
fan5:          0 RPM  (min =    0 RPM)
temp1:       +29.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:       +56.0°C  (low  = +127.0°C, high = +60.0°C)  sensor = thermal diode
temp3:       +82.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
cpu0_vid:   +1.550 V

```

---

### Post by TenPlus1 on 2009-02-18
AMD Athlon 2400+ XP running at 46oC...

---

### Post by sdennie on 2009-02-18
> **boblizar said:**
> what is the name of the package that has the acpi -t command?

i have lm_sensors working, but have a conkyrc that uses acpi commands and would like to get acpi working also.

this is for a phenom am2+ 9950 quad core with 8gb of ram.  im asking the package name since im a linux from scratch person =)


On Ubuntu 8.04, the package is called "acpi":

```

$ dpkg -S /usr/bin/acpi
acpi: /usr/bin/acpi

```

---

### Post by matnojje on 2009-05-26
Well this can't be good?

i get:
    Thermal 1: ok, 69.0 degrees C
     Thermal 2: ok, 78.0 degrees C
     Thermal 3: ok, 0.0 degrees C

it's a gaming laptop.

---

### Post by crazybuntu on 2009-06-02
my laptop is in the  46-50's  with wifi on and compiz, browsing this forum

---

