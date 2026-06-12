---
title: "Viewsonic battery problem, Viewpad 10"
date: 2012-01-19
forum: Hardware
---

### Post by tcallahan1982 on 2012-01-19
This is my first Ubuntu install, and after a couple weeks of tuning, I'm loving it. Windows always sucked, and Mac was way too expensive. I got a Viewpad when they first came out, thinking it would be perfect, but I got the last one in the store, basically second hand. Won't do that again!

I'm now running Ubuntu 11.10 with the Gnome 3 shell, and its great, but for one thing. I have a battery problem.

When I take my Viewpad off of the charger, I immediately get two Identical warnings about low battery. It does not matter what the battery icon says. Within about a half hour, the machine shuts down. 

I ran acpi (found on another forum) and got this:

user@computer:~$ acpi -V

Battery 0: Unknown, 99%
Battery 0: design capacity 3000 mAh, last full capacity 2412 mAh = 80%
Adapter 0: on-line
Thermal 0: ok, 40.0 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 94.0 degrees C
Thermal 0: trip point 1 switches to mode passive at temperature 84.0 degrees C
Cooling 0: LCD 5 of 9
Cooling 1: Processor 0 of 3
Cooling 2: Processor 0 of 3

That's with it plugged in. If I unplug it, I get:
 

 user@computer:~$ acpi -V 
 Battery 0: Discharging, 99%, 03:35:09 remaining 
 Battery 0: design capacity 3000 mAh, last full capacity 2490 mAh = 83% 
 Adapter 0: off-line 
 Thermal 0: ok, 39.0 degrees C 
 Thermal 0: trip point 0 switches to mode critical at temperature 94.0 degrees C 
 Thermal 0: trip point 1 switches to mode passive at temperature 84.0 degrees C 
 Cooling 0: LCD 5 of 9 
 Cooling 1: Processor 0 of 3 
 Cooling 2: Processor 0 of 3 
 

  
 Since adding acpi, it only gives one alert, rather than 2, but still throws the alert immediately on unplugging the cable.
 

 Any ideas? I'm very green at this, so step by step if possible.
 

 Thanks!

---

### Post by tcallahan1982 on 2012-01-20
Looking around, this seems to be a problem with upower? Anybody working on a fix, point me in the right direction? Is there a quick fix that I could revert to a different power control?

---

