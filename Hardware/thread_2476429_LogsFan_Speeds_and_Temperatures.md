---
title: "Logs:Fan Speeds and Temperatures"
date: 2022-06-26
forum: Hardware
---

### Post by wyattwhiteeagle on 2022-06-26
Are there logs of fan speeds and temperature's?

Something happened to me and I jumped sending my laptop flying across the room.
Now my laptop fan is noisy and loud when it is running.

---

### Post by guiverc on 2022-06-26
I'm not aware of any; though some temperature warnings can appear in normal system logs.

I've had trouble with laptop fans before, and I always added package(s) to the system, so I could get what I needed (logs etc) that confirmed I needed to replace a cpu fan; once the fan was replaced I'd disable the logging and never need it again on that laptop.

I'll not provide any package details; as I don't think I've needed to do that since Lubuntu switched to LXQt (ie. many years).  I also believe the package that worked best on one laptop, was not the best for others... ie. different brands/models of motherboard can get the best temperature readings using different methods.

---

### Post by Yellow Pasque on 2022-06-26
What model laptop is it?
You should at least be able to get temp output with:
```
sensors
```
And then you can monitor it with conky or something like that. Fan speeds are trickier, especially on laptops. It really depends on the model whether you can access it through the OS or not.

> Now my laptop fan is noisy and loud when it is running.

Is it making strange/unusual noises or just running a lot faster (and thus, noisier) than it used to? If the former, my concern would be that you physically damaged the fan. If the latter, I'd be concerned that the thermal paste/pad between the CPU got compromised, especially if you're seeing high temps.

---

### Post by wyattwhiteeagle on 2022-06-26
> **Yellow Pasque said:**
> What model laptop is it?
Dell Latitude E5400 Laptop
Lubuntu 22.04 LTS (Jammy)


> **Yellow Pasque said:**
> 
You should at least be able to get temp output with:
```
sensors
```
I entered sensors into the Qterminal and got "not installed. You can install lm-sensors"


> **Yellow Pasque said:**
> And then you can monitor it with conky or something like that. Fan speeds are trickier, especially on laptops. It really depends on the model whether you can access it through the OS or not.
I was looking into conky for a very thorough and very specific monitoring tool for performance.
I think I really, really need it for sure now.



> **Yellow Pasque said:**
> Is it making strange/unusual noises or just running a lot faster (and thus, noisier) than it used to?
If the former, my concern would be that you physically damaged the fan.
If the latter, I'd be concerned that the thermal paste/pad between the CPU got compromised, especially if you're seeing high temps.

I took it apart...the laptop then the fan...
cleaned all the dust and lint out as best I could...
shook out anything that might've came loose...nothing fell out.


The fan isn't directly over the cpu.
The cpu is covered by a metal x-guard with a copper-colored rod attached.
That rod travels through the inside of the housing to the vent directly in front of the fan.


When I re-assembled the fan and then the machine and turned it on...the fan isn't as loud but it isn't as quiet as before.


My opinion...
The laptop is still usable.
When the laptop hit, dust that was inside the fan got knocked around and some of the dust particles is now inside the fan motor.
Physical damage is being done to the fan.


1. Shut down when not in use. (I usually leave mine running unless I'm rebooting)
2. Try to avoid using app's that cause a high cpu temperature.
3. Replace the fan or the laptop ASAP.


I actually need a new laptop.

---

### Post by wyattwhiteeagle on 2022-06-26
*UPDATE*
Conky didn't work correctly...
Went with Cacti

---

