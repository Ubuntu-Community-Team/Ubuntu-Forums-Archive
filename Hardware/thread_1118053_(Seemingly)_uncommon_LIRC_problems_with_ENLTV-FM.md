---
title: "(Seemingly) uncommon LIRC problems with ENLTV-FM"
date: 2009-04-06
forum: Hardware
---

### Post by schmidtbag on 2009-04-06
For starters, I have an Encore ENLTV-FM TV tuner and it has its own built in IR receiver, and it came with a pretty nice remote which I want to use.

As nearly everyone knows, the numbers, arrows, mute, sleep, and enter will always work without installing LIRC.  Like everyone else with a remote, I wanted more functionality.  So, I installed lirc, as well as the gnome-lirc-proporties.  With lshal, I was able to find my remote's device was "/dev/input/event5".  I later installed "inputlirc", which I noticed makes it so I can't use the same buttons as before (except arrows) but I can use everything else, which is weird..  So in "Remote Control Proporties" I chose the following:

Manufacturer: Generic
Model: Serial Port Receiver
Device: /dev/input/event5
[ ] Use supplied remote control
[O] Use different remote control
Manufacturer: Unknown
Model: enltv

If I change ANYTHING, whenever I start up that program it says my configuration is wrong, otherwise it just starts up fine if I select unknown with enltv.  If I pick "enltv" and then customize the setup, changing the manufacturer and model fails.

Even though the program can correctly recognize the (limited) buttons I press, no other program recognizes them, and anything I do to customize the remote it says "Failed to initalize hardware".  Before installing "inputlirc" it recognized nothing.



Why is this so difficult?  The remote works.  I know which event it is.  Why does this fail for inexplicable reasons?  The default serial port is useless.

---

### Post by schmidtbag on 2009-04-07
bump

---

### Post by schmidtbag on 2009-04-08
not even a direciton as to where i could go?

---

