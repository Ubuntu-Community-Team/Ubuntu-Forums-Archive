---
title: "Ubuntu, an external monitor, and NVidia .... HELP!"
date: 2010-05-01
forum: Hardware
---

### Post by X-Legs on 2010-05-01
When a Macbook Pro 4,1' s screen broke, I decided to get an external monitor in order to make the laptop useful, as that would be cheaper than a screen repair. I have a dual boot OS X/Ubuntu 10.04 system now. The Ubuntu default driver worked well, but I am a sucker for wobbly windows, and so I decided to install the NVidia restricted driver.

I had three choices: 2 of them were NVidia and I chose the one tagged [recommended]. It asked to reboot and I did. The problem was that the display stopped showing up on the big external display connected to the laptop. I was able to discern that the NVidia driver disabled my external monitor. Changing this was a simple matter of changing preferences.  

Unfortunately, the actual laptop's display is broken. Therefore, I cannot change the preferences with the laptop itself. Is there a way to use the Live CD and edit some configuration file so that the driver will successfully display on my external monitor? 

My graphics card is an NVidia GeForce 8600M GT
My display is a Dell VGA monitor with 1600x900 resolution
My Ubuntu version is 10.04.

Any help is appreciated. Thanks

---

### Post by dino99 on 2010-05-01
you says " The Ubuntu default driver worked well"

so undo your latest changes  :P

should only have nvidia-current, nvidia-current-modaliases, nvidia-common and nvidia-settings installed, 

remove/purge with synaptic all the others non ubuntu nvidia drivers (remove ppa if you have)

---

### Post by X-Legs on 2010-05-02
I don't get compiz with the default driver. I would like to have compiz ability, if that is possible.

---

