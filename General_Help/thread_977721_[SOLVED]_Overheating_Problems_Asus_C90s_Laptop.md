---
title: "[SOLVED] Overheating Problems Asus C90s Laptop"
date: 2008-11-10
forum: General Help
---

### Post by blazercist on 2008-11-10
Hey guys, I have a problem.  I'm trying to use my Asus C90s Laptop as an HTPC...

Specs: Intel Core2Duo @ 2.13GHz
       2GB RAM
       Geforce 8600GT 256MB
       120 GB HDD

Its got an HDMI->DVI output which I run to my 42" Sony Plasma.  I got a wireless keyboard for it from Adesso which works fine.  And since the TV is DVI I also run an SPDIF cable for sound.

nvidia-settings thermal monitor says at idle the card is running at a whopping 96C,  it has a kill switch at 110C.  The lappy idles just fine and I can surf web and check e-mail without a hitch.  But if I run a fullscreen movie after about 20 minutes video will go dead, I still get sound but the video just turns off.  CTRL+ALT+BACKSPACE doesn't fix, the only way to get video back is to restart.  I'm running 8.10, I just recently upgraded from Hardy, because I read that some laptops were running cooler with Intrepid.... but alas no joy.


I was wondering if there was any advice someone could offer to lower the temp.  Please, keep in mind that I'm not blocking the air intake/outtake or any of the fans and the fan are running.  I was considering "undervolting" but it seems very complicated and doesn't guarantee any results.  Any other options? Preferably software fixes if possible.  Thanks in advance.

---

### Post by blazercist on 2008-11-11
Nobody has any suggestions?  Is there any information I need to add?

---

### Post by hardyn on 2008-11-11
will it run the correct temp under windows, or another distro?


I have had a couple of asus notebooks, and none of them have been quiet or cool, you may want to inspect the mechanical aspect of the cooling; give the fan(s) a good blow out with some compressed air (jam the fan if possible as not to overspeed).

if the notebook is outside warranty inspect the heat pipe(s) to make sure that it is still making good contact with the processor or video, inspect for pinholes around solder connections of the heat pipe.  the problem is likey software related as such heat pipe failures are not common, but arn't unheard of either.

---

### Post by eldragon on 2008-11-11
check what you got in 
```

/proc/acpi/thermal_zone/*/

```

ive got some cooling issues under intrepid too, when this bug appears, the thermal_zone dir is empty, otherwise, i can check temps and stuff.

not an answer, but a finger pointing somewhere :D

---

### Post by blazercist on 2008-11-11
Thanks for the replies guys,  I'm going to double check the hardware when I get home.  

@eldragon: I had the same problem under Hardy, I went to Intrepid thinking it would help solve the problem to no avail, I'll run that command when I get home.

---

### Post by brandon88tube on 2008-11-11
Yeah, I have a similar problem, but mine wants to fry itself while its idle.

---

### Post by blazercist on 2008-11-11
Unfortunately I don't have a dual boot so I can't test Windows or any other OS.  I could install a different distro but I would rather not.

---

### Post by brandon88tube on 2008-11-11
Why can't you dual boot? That would be best to check and see if Windows works for you. If it doesn't then it sounds like a hardware problem. If it does work on the other hand then its a problem with Ubuntu, like I have.

---

### Post by blazercist on 2008-11-11
brandon88tube, because I really don't want to install Windows?  But you are right, I'm trying to avoid partitioning and installing Windows at all costs.

---

### Post by brandon88tube on 2008-11-11
Don't really know what to tell you if you don't feel like partitioning and installing Windows. I know what its like not to want to install stuff unless I ABSOLUTELY need to and then I still fight with it.

---

### Post by blazercist on 2008-11-12
Ok heres some info:

```
cat /proc/acpi/thermal_zone/TZ00/*
```

polling frequency: 30 seconds
state: ok
temperature: 53C
critical (S5): 110C
passive: 100C: tc1=2 tc2=10 tsp=10 devices=CPU1

But the core temp in nvidia-settings thermal monitor is 98C, meaning to me that its the video card getting hot and not the CPU.

The temps stay here as long as the box is idle, but when I play video these temps are slowly rising.

I have never encountered this before, I'm used to the CPU running hot and overheating not the GPU.  I have yet to open the case and examine the GPU to see if it perhaps has a fan or heatsink thats been abstructed somehow.  That will be my next step.  Somehow though I doubt that this GPU has a fan because, well, its a laptop.  If it doesn't have a fan or if it does and the fan isn't broken then I don't know what to do.

---

### Post by blazercist on 2008-11-20
So, just incase anyone is interested I have found the "solution".

Well, I'm not sure how I arrived at the solution, I'm not sure how or why it worked either, I just know it does fix the problem, at least substantially.

All I had to do was to change the opacity of my desktop cube in compiz to 100% opaque.

It's weird I don't know why... I had my cube set to be 25% opaque both when idle and when rotating, changing it to be 100% opaque when idle brought the temps down a good 10C on average.

---

