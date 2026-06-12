---
title: "Touchpad problem"
date: 2009-11-07
forum: Hardware
---

### Post by sozgen on 2009-11-07
Hi, I want to turn off my laptops touchpad while I am typing. I tried Community help about Synaptics but there are some problems: Touchpad is working properly but when I try to run syndaemon I get an error of "Unable to find a synaptics device". In 9.04, when I tried to run syndaemon it gave a warning "Can't run, maybe shmconfig is not enabled" but now it does not say such  thing; only says that can not find driver. I also did edited the shmconfig.fdi file under /etc/hal//policy  (there was no such file only a preferences.fdi file so i created shmconfig.fdi and inserted xml code there) as told but that did not work neither.
When I use xinput list I get:


"ImPS/2 Elantech Touchpad"	id=7	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 7
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"Razer Razer Diamondback Optical Mouse"	id=8	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 15
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
        Axis 1 :
		Min_value is -1
		Max_value is -1 
		Resolution is 1



There is also more to that but I did not thought it was necessary.

tl;dr I want to turn off my touchpad while I am typing end tutorial at ubuntu synaptics help did not helped at all, I would be glad if you could help.(Even it's ok for me to make a keybind to turn it off and on. I just hate when it randomly jumps to some point accidently while typing)

---

### Post by orengolan on 2010-01-25
sozgen,

There is a problem with Elan touchpad.
I submitted the bug on Launchpad:
[https://bugs.launchpad.net/ubuntu/+s...cs/+bug/512192](https://bugs.launchpad.net/ubuntu/+s...cs/+bug/512192)

Please go there and change the status to 'Confirm' so Ubuntu developers will understand that it's a hardware issue and not something specific to me.
Also mention your hardware.

Thanks you so much!

---

