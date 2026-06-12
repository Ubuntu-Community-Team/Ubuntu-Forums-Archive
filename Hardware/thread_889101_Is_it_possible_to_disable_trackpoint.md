---
title: "Is it possible to disable trackpoint?"
date: 2008-08-13
forum: Hardware
---

### Post by vodafone on 2008-08-13
I'd like to disable the trackpoint on my Toshiba laptop, could someone tell me how to configure this? Advices are appreciated! thanks!

---

### Post by kebajonathan on 2008-08-27
I want to disable it too because it always makes my mouse pointer go to the upper left corner of the screen and I can't use the mouse (even with the synaptics tp) after that...

---

### Post by kosmiciatakuja on 2008-08-27
This may not be the easiest but you could try this:
sudo nano /etc/X11/xorg.conf

Locate the ServerLayout section, it should look like this:

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Synaptics Touchpad"
    InputDevice    "Configured Mouse"
EndSection

And comment out this:
   InputDevice    "Synaptics Touchpad"

with # in the beginning.

---

### Post by kebajonathan on 2008-08-27
well, this would disable the touchpad (but I need it) whereas it's the trackpoint that doesn't work correctly any more.

---

### Post by kosmiciatakuja on 2008-08-28
oh, sorry :)
I confused the two. 

Is trackpoint the little joystick somewhere around the keyboard? 
If so, *in theory* I think you should be able to turn it off by saying
```
synclient GuestMouseOff=1
```
on the command line
However, this does not work for me (Lenovo R61). 
I don't know any other way though, sorry :(

Quoting man synaptics:
>  GuestMouseOff (Bool)
              Switch on/off guest mouse (often a stick).

For it to work I believe you should have SHMConfig "True" in your xorg.conf in the Synaptics InputDevice section. 

And, if it works, you can just add it there as an option, like
```
Option "GuestMouseOff" "true" 
```

---

### Post by kebajonathan on 2008-08-28
Yes, the little "joystick"-thing in the middle of the keyboard is the trackpoint. Unfortunately, your suggestion didn't work, I don't understand why :( Thanks anyway. If you have any other suggestion...

---

### Post by kebajonathan on 2008-08-28
the drifting trackpoint seems to make so many interrupts that the synaptics tp hangs... How can I de-activate that? It's hardware related but I should be able to do something with the driver, right?

---

### Post by kebajonathan on 2008-08-29
I solved it by putting some sticking tape on the four contacts (on the left) of the keyboard and by doing so block the trackpoint mouse. By doing so, I have disabled it on the hardware level. The contacts had an other colour so that was quite easy to find. I can now use the touchpad without any problems... Hope this helps anybody

---

### Post by eauque on 2009-07-12
> **kebajonathan said:**
> I solved it by putting some sticking tape on the four contacts (on the left) of the keyboard and by doing so block the trackpoint mouse. By doing so, I have disabled it on the hardware level. The contacts had an other colour so that was quite easy to find. I can now use the touchpad without any problems... Hope this helps anybody

YES!! Thank you thank you thank you!! This is how to disable the trackpoint! I have an old Dell so the procedure was different. I unplugged a small ribbon cable from the main keyboard connector and now, no more wandering cursor!

---

