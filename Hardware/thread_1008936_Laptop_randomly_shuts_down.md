---
title: "Laptop randomly shuts down"
date: 2008-12-12
forum: Hardware
---

### Post by averageidiot on 2008-12-12
Running 8.10 my P4 laptop and for some reason, after a little bit of use ~30 min-2 hrs. It randomly shuts off. Basically it does exactly what it would do it you went and shut it down manually. Doesn't show any error messages, it just shuts down. I dual boot XP and this doesnt occur on XP at all. The only thing I can think of is that it might be temperature related as my P4 does get pretty hot but its fairly expected of it. Anyone have any ideas?

---

### Post by sdennie on 2008-12-12
This could be related to the power manager settings and it incorrectly detecting your battery charge/AC power state.  Try going to System->Preferences->Power Management and making sure no auto-shutdown commands have been set.

---

### Post by averageidiot on 2008-12-12
The only thing was when battery is critical low. I changed it but i dont think this is it.

---

### Post by damis648 on 2008-12-12
Open a terminal and enter
```
sudo apt-get install sensors-applet
```
and let it install. Afterward, right click one of your panels and then add the Sensors Applet to the panel. It will display the temperatures. Report them back to us.

---

### Post by averageidiot on 2008-12-15
Yeah, same shutdown problem was happening. I'll install that app and see if I can get some temperatures out of it. I suspect this to be the problem, just wondering if there was a way to maybe increase the threshholds. I think i'll buy a can of compressed air too to maybe clean it out. Thanks guys.

---

### Post by jcsteele on 2008-12-15
```
$ acpi -V
```

Also does the trick, and might tell us something about ACPI and your laptop as well....copy paste the results when you enter the command above into a terminal (Applications->Accessories->Terminal)

What you SHOULD expect to see (depending on your hardware of course):

```
jcsteele@neuron:~$ acpi -V
     Battery 0: Full, 100%
     AC Adapter 0: on-line
     Thermal 0: ok, 46.0 degrees C
     Thermal 1: ok, 48.0 degrees C
     Cooling 0: LCD 0 of 7
     Cooling 1: LCD 0 of 7
     Cooling 2: Processor 0 of 10
     Cooling 3: Processor 0 of 10
     Cooling 4: Fan 0 of 1
```

If a fan isn't functioning, or your thermal sensors are reporting some extreme values (> 75C) you might want to consider not running ubuntu very long - your system might be overheating.  Post what you get and let us know.

---

### Post by averageidiot on 2008-12-15
Battery 0: Charging, 98%, 00:00:04 until charged
  AC Adapter 0: on-line
     Thermal 0: ok, 80.0 degrees C
     Cooling 0: Processor 0 of 10

---

### Post by jcsteele on 2008-12-16
Yeah, that would explain why your machine is shutting down.  80C is really hot, so your machine is shutting itself down to prevent damage.

I am not sure what options you have, but I would advise you to not run the machine - you will eventually just burn up everything and be left with an expensive paperweight.  You can try it again if support is added/improved for your machine in the future, but for now I don't have any other advice other than start googling for your specific hardware on linux, etc. and see what others have come up with as a solution.

---

