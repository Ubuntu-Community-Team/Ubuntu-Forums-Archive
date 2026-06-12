---
title: "how to change CPU temp &quot;trip_points&quot;"
date: 2006-11-29
forum: Hardware &amp; Laptops
---

### Post by mertin on 2006-11-29
hi everyone

i just installed the latest ubuntu on my samsung xtc x10 and it works pretty well. i love it! The Problem is: it gets really hot to a point where i am scared of risking damaging my hardware or my body (when on lap)

```
acpi -t
```

*never* shows anything above 46°C but it is seriously getting hot.

```
cat /proc/acpi/thermal_zone/THRM/trip_points
```

returns:

```

critical (S5):           120 C
active[0]:               65 C: devices=0xcff5d928 

```

I don't know if "active[0]" hints me that the actual temperature is 65°C but is think 120°C as critical is ridiculous... how can i move the trippoint to a more reasonable value and how can i make fan kick in earlier? Sometimes it goes on but the it dies rather quick... this is really sad. I've read a lot of posts here dealing with the matter but there seems to be no real solution at hand. 

Where can i lower the settings to make my fan spin at the right temp???

(i also guess the throttling of my cpu doesn't work at all: **powernowd** has 5 steps, while **cat /proc/acpi/processor/CPU0/throttling** shows 8 steps and always says that T0 (step 0) is the current step.)

cheers

mertin

---

### Post by dmartinsca on 2006-11-29
For changing trip points, you'll need to open a terminal and switch to the root user by running **sudo su -**
_Now be careful, any command you type is run with root privledges_

Be aware that you may have more than one thermal zone, you'll know you do if there is more than one directory under /proc/acpi/thermal_zones. If there is more than one you should check the output of **cat trip_points** for each one to get an idea of what they do and when they should trigger.

[LIST]
[*]critical zones usually turn off the computer.
[*]passive zones will usually throttle the cpu (these are the 8 steps you noticed in the throttling file, it is not frequency scaling)
[*]active zones usually control fans.
[/LIST]

You change the trip_point values by running **echo -n "x:y:z:a:b" > trip_points** where x,y,z,a, and b are the values in celsius for the corresponding trip points. The format is critical:hot:passive:active[0]:...:active[n]

Now, the weird thing is, it seems you need to have 5 fields, so x,y,z,a, and b are all required but if your laptop doesn't have a corresponding trip point just put a zero. What does the hot field represent/do? I don't know!

So mertin, for your laptop you'll want something like **x:0:0:y:0**, picking appropriate values for x and y. Also, as a briefly said above, the 8 states you see in the throttling file are not cpu frequency scaling. These states actually put the cpu to sleep for a certain percentage of each cycle. My experience with this is that everything gets really jumpy & quite delayed. If these states were controlled by a program along with frequency scaling there is a chance you'd get better battery life & not take such a performance hit, but i've never looked into setting this up.
If you want to check the frequency scaling is working, right click on a panel, choose Add to Panel.. and pick the CPU Frequency Scaling Monitor (assuming  you're using Gnome)

BTW, I think this is the site I originally got this info from: [http://acpi.sourceforge.net/documentation/thermal.html](http://acpi.sourceforge.net/documentation/thermal.html)

---

### Post by Johan! on 2006-11-29
> **mertin said:**
> hi everyone

i just installed the latest ubuntu on my samsung xtc x10 and it works pretty well. i love it! The Problem is: it gets really hot to a point where i am scared of risking damaging my hardware or my body (when on lap)

```
acpi -t
```

*never* shows anything above 46°C but it is seriously getting hot.



Are you sure the temperature, reported by acpi -t, is OK?
If it's not accurate, it's useless to change the trip points.

(My PC always shows 40°C when I run acpi -t, but the lm-sensors package shows the right temperature)

---

### Post by dmartinsca on 2006-11-29
> Are you sure the temperature, reported by acpi -t, is OK?
If it's not accurate, it's useless to change the trip points.

(My PC always shows 40°C when I run acpi -t, but the lm-sensors package shows the right temperature)

That's a good point. lm_sensors is probably a more accurate temperature, however, the trip points trigger based on the temperature shown by acpi -t, which is actually the temperature taken from /proc/acpi/thermal_zone/<zone>/temperature.

Something i forgot to mention before, you'll have to make the changes to the trip_zones files each time you boot.. I'm new to ubuntu so i'm not sure how to do this automatically. Sorry!:)

---

### Post by mertin on 2006-11-30
hi everyone, thanks for your replies! 

@johan! : i got lm-sensors with "apg-get install lm-sensors", it downloaded and installed but i cannot use it.. ah well

@dmartinsca : thanks for all the advice! I knew about the sudo su thing already from this forum. Unfortunatly i cannot reset the trip_points like you showed me:

```

root@martin-laptop:/var# cat /proc/acpi/thermal_zone/THRM/trip_points

critical (S5):           120 C
active[0]:               65 C: devices=0xcff5d928 

root@martin-laptop:/var# echo -b "65:0:0:50:0" > /proc/acpi/thermal_zone/THRM/trip_points 

bash: echo: write error: Invalid argument

```

as you wrote i have no idea what to put where with those settings for trip_points, and the command obviously failed. But i managed to put the cpu freq scaling monitor and according to it the throttling seems to work fine. Any more ideas?

**edit!**
```

root@martin-laptop:/var# echo "75:0:0:50:0" > /proc/acpi/thermal_zone/THRM/trip_points 

root@martin-laptop:/var# cat /proc/acpi/thermal_zone/THRM/trip_points critical (S5):           75 C
active[0]:               50 C: devices=0xcff5d928 

```

i left the **-l** switch away and it worked... but the laptop is still getting hot. Any suggestions how i could force it bring on the fan? and by the way is there any way at all to get the fan started if i only have the 2 trip_points? i am wondering: if i only have 2 trip_points, "critical" and "active[0]", at which point would the fans be started? 


instead of guessing i now just set the "active[0]" value to lower than my current temp(according to acpi -t)... but *nothing* happens... i am really frustrated. everything works so well but the heat is seriously disturbing my experience. i wouldn't even mind if the fan was running all the time because it isn't too noisy but getting the temperature check to work would be great!


ps: will there be any problems if i double the ram?

---

### Post by Johan! on 2006-11-30
Try searching for lm-sensors in the how-to threads of this forum ;)

---

### Post by mertin on 2006-11-30
well i found this nice app for the panel: [http://computertemp.berlios.de/](http://computertemp.berlios.de/)

it will display the current temperature according to acpi. if i now can find out how to force the fan on i will have my own cooling solution (computertemp supports running commands on hitting a certain temp)

i also installed lm-sensors according to the tutorial here and rebooted but i still can't use it

---

### Post by dmartinsca on 2006-11-30
Well, the fan may just be controlled by the BIOS, in which case you can't do anything about it. On the other hand, you may be able to turn the fan on or off by doing **echo 0(on) or 3(off) > /proc/acpi/fan/FANx/state**
I don't know if 1 or 2 would do anything, maybe different speeds? I don't have a laptop to test this on, my fan is simply controlled by the BIOS according to system load.

---

