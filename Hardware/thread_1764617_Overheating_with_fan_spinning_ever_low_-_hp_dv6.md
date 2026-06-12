---
title: "Overheating with fan spinning ever low - hp dv6"
date: 2011-05-21
forum: Hardware
---

### Post by askrym on 2011-05-21
hi everybody

i got an HP Dv6-3149sl laptop with kubuntu 10.10 amd64

while i'm writing this, my cpu sensor detects 70° celsius , the pc is actually idle (below 5% cpu activity) 

i played for 3 minutes (maybe less) super smash bros on dolphin gamecube emulator, i had to suddenly close it as soon as i noticed that the 

temperature was above 100° , i touched the chassis right below the cpu place and it was actually extremely hot i had to recede.

i wanted to check this out a little better so i ran:

```
 paolo@dv6:~$ acpi -V
Battery 0: Full, 100%, rate information unavailable
Battery 0: design capacity 5100 mAh, last full capacity 4896 mAh = 96%
Adapter 0: on-line
Thermal 0: ok, 69.0 degrees C
Thermal 0: trip point 0 switches to mode hot at temperature 105.0 degrees C
Thermal 0: trip point 1 switches to mode passive at temperature 130.0 degrees C
Cooling 0: LCD 0 of 10
Cooling 1: LCD 10 of 10
Cooling 2: Processor 0 of 10
Cooling 3: Processor 0 of 10
Cooling 4: Processor 0 of 10
Cooling 5: Processor 0 of 10
Cooling 6: Processor 0 of 10
Cooling 7: Processor 0 of 10
Cooling 8: Processor 0 of 10
Cooling 9: Processor 0 of 10
paolo@dv6:~$ 
```

it looks a bad setting of trip-points to me.
then i considered that it's natural that the cpu is reaching such high temperatures because the fan is spinning always at the minimum speed (i hardly  hear it working)

did somebody have already such problems? maybe trying to change the settings to the temperatures/fan.speed parameters in order to get the cpu less hot?

thanks for the help:)
ps. i'll keep on looking up through google in the meantime, i'll post here if i find something useful for those who have the same problem
ps.ps. sorry for not posting in english originally, it was 5am and i messed up with ubuntu.it forum :(

---

### Post by asd1618033 on 2011-05-22
Hai scritto in italiano sul forum internazionale :| Usa [http://forum.ubuntu-it.org/](http://forum.ubuntu-it.org/)
ho problemi simili, sentiamoci in qualche modo. vorrei sapere la tua configurazione. ti mando una mail se riesco.
--------------------------------
This is an international forum board.
Use [http://forum.ubuntu-it.org/](http://forum.ubuntu-it.org/)

---

### Post by askrym on 2011-05-22
@asd1618033

could you send me msn contact or googletalk one through private message?
i have some problems replying to you by P.M. here.
bye :)

---

### Post by askrym on 2011-05-22
I've  run the emulator with the same game on windows7 for half an hour, the  CPU heats up quickly up to 86 ° and stays stable until i quit the game , while the fan spins as fast as it  should.

------
in kubuntu:

i have a "ATI Mobility Radeon HD 5650" ....  [LEFT]installed and currently in use proprietary ATI drivers downloaded from their website , last release[/LEFT].


-> / Proc/acpi/thermal_zone/TZ01/trip_points

> 
hot (S4):                105 C
passive:                 130 C: tc1=2 tc2=5 tsp=50 devices=CPU0 CPU1 CPU2 CPU3 CPU4 CPU5 CPU6 CPU7 


I think that the only problem is that the temp. threshold isnt ok
while in windows when the CPU is over  80 degrees , the fan starts spinning very fast , when in ubuntu instead , the acpi controls wait that the temperature reaches over  100 degrees before (presumably) incrementing fan speed (i didnt want to risk reaching higher temps. to check it out). 


so i tried to change the trippoints:

> 
paolo@dv6:~$ sudo echo -n "100:90:30:70" > /proc/acpi/thermal_zone/TZ01/trip_points 
echo: write error: Input/output error


(i had the right permissions)
after making some more searches i found out why i couldnt change that:

[http://lwn.net/Articles/244595/](http://lwn.net/Articles/244595/)

it seems that in recent kernels,  the change of these parameters is no longer permitted, the reasons are listed in the linked webpage. 
 [LEFT]...[/LEFT] but now I wonder ... [LEFT][/LEFT]how do I keep the CPU temperature enaugh low if i do not  have control over the fan speed at certain temperature thresholds? 
  [LEFT][/LEFT]...why do I need to have control over this? [LEFT]....[/LEFT] ....[LEFT][/LEFT] for i deduct that the  component that should handle this matter automatically does not work because the  cpu temp. floated over 100 degrees .... luckily I found out that before incurring in some serious damages and quitted the app.  ......[LEFT][/LEFT] Perhaps if it had continued to rise it would have shut down the PC to protect hardware, but certainly i do not want to find it out. [LEFT][/LEFT]
The fact is that it reached 100°+  is because there's something handled in a wrong manner for sure .... and even after reaching 100° , the fan was still spinning low ..

some suggestions?

---

### Post by askrym on 2011-05-22
since the temperature of the cpu with heavy workload isnt so low in windows either (it easily reaches 85°.. & sometimes around 90° but never more .... [only with linux it reached 100° due to a sleepy fan:mad:]) i decided to investigate a little more ....

anyway .. i've been searching some general info about my pc ... hardware , chassis , cooling .... well it seems that except for my specific problem about the fan not spinning enaugh for fine-cooling  , this hp laptop model and some other have their own over-heating problems (independent from O.S.), there are many owners complaining about overheating and the fact that they are forced to use additional cooling systems (like the lifted dock with embedded fans) ....

so, in conclusion .... the insane nature of overheating is due to HP design , which i find very "smart" 
and about linux , its only "fault" is just that the thresholds arent so well set ... and the fan spinning slowly lets the pc reach higher temps than those under windows.
still didnt find a remedy for changing the thresholds and i'm not planning to do more searches since the absolute major part of fault has to do with HP manufacturer.

i'm sorry for those people with my same problem but it seems there isnt an easy and exhaustive solution. :(

---

