---
title: "joymap and the Saitek X55"
date: 2015-01-06
forum: Hardware
---

### Post by Ovadex on 2015-01-06
Hi all!
I'm working on using joy-map to take my X55 joystick and throttle and combine them into one virtual controller. I am nearly there but have hit a couple of sticking points.

I have it all working to a degree but whenever I run loadmap to start the mapping the joystick controls the mouse and the joystick isn't mapped to a js* device. It is left as an event device. It does create a js2 device (js0 and js1 being the physical controls) but it is mapped to the joymap code device instead of the joymap joystick 0 device. This of course means I can't access it as a normal game controller.
The code device doesn't relay any control inputs.

I'm hoping there is someone here that has some experience with joy-map, my efforts to find info online have been mostly fruitless. 

I have all my configs and info on my pastebin. The only stuff on there relates to this endeavor.

[pastebin.com/u/ovadex]("http://ubuntuforums.org/pastebin.com/u/ovadex")

Thanks to anyone that may have some suggestions on this.

Ova

---

### Post by alexandre-hardy on 2015-05-11
> **Ovadex said:**
> Hi all!
I have it all working to a degree but whenever I run loadmap to start the mapping the joystick controls the mouse and the joystick isn't mapped to a js* device. It is left as an event device. It does create a js2 device (js0 and js1 being the physical controls) but it is mapped to the joymap code device instead of the joymap joystick 0 device. This of course means I can't access it as a normal game controller.
The code device doesn't relay any control inputs.


Hi,

Somewhere along the line the Linux kernel became more fussy about input and stopped detecting devices with large numbers of buttons as a game controller. At least, that is how I remember it (I recall fixing it for a raspbian user). I believe that should be fixed in the latest version of joymap (joymap-0.2)? It would be great if you could provide the output of "cat /proc/bus/input/devices" for me to have a look at. I'm not very active in maintaining this code anymore, but will make an attempt from time to time to keep it working.

Kind regards
Alexandre

---

