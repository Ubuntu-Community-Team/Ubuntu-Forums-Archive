---
title: "Nvidia 940M on 12.04"
date: 2015-12-03
forum: Hardware
---

### Post by felix37 on 2015-12-03
It is possible at all to use a 940M gpu with Ubuntu 12.04?

Background: So i got this Laptop with a discreet Nvidia 940M graphic card for work. Sadly i have a few premises i can't change:

1. I have to use Ubuntu 12.04 
2. I have to use the Nvidia card/ driver because a program i have to use wont work with either amd or intel gpus and software render is to slow
3. I cannot change or update the software (gazebo 1.9) i have to use it as is

As it turns out anything newer than the 7xx Nvidia series seems to be not supported by the 12.04 as i would need the nvidia-346 driver but the latest i can install is nvidia-340. 
I can't install it even if i use add-apt-repository  to add the dev repository for nvidia. If i try to install say nvidia-346 with apt-get it tells me [FONT=arial]"[COLOR=#111111]Package [/COLOR]nvidia-346[COLOR=#111111] has no installation candidate[/COLOR]"[/FONT]

If i download the nvidia-346 or newer from nvidia, kill the xserver and install it, everything seems fine. If it isn't done by the driver installer already i use "nvidia-xconfig" to setup the xconfig. I reboot and i get an unchangeable 640x480 resolution as soon as the driver is loaded.
Using nvidia-smi tells sows that the gpu ought to be in working order with the proper driver installed.
Installing bumblbee doesn't change a anything.

---

