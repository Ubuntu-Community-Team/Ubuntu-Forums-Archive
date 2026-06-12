---
title: "Computer freezes after returning from standby"
date: 2010-08-10
forum: Hardware
---

### Post by Berniebln on 2010-08-10
Hello there,

I have the following problem: if I turn the computer into stand-by mode, it will properly do this, all lights go out except for the power light which starts blinking.

But when I try to wake it up from sleeping, the following happens: The screen backlight turns on, but the screen itself stays black, I can see the white mouse pointer somewhere on the screen, but the system froze, so when I move the mouse, the pointer won't move. Also, pressing caps lock or num lock does not toggle the correspondent LEDs. Then, I can only shut the computer down by keeping the power button pressed for 5 seconds.

Anyone any ideas of how to fix this? ;-)

I'm using an Asus laptop, X72TL, with an AMD Turion 64 bit dual-core processor, and ATI Mobility Radeon HD 3400 Series, with the FGLRX driver. My linux is ubuntu 10.4, 64 bit version.

Bernhard

---

### Post by Berniebln on 2010-08-10
Hi again,

I've just installed µswsusp (via Synaptic), it didn't solve the problem, but there is a little difference to the behaviour my laptop showed before:

Now, I can not only see the mouse pointer when returning from standby, but also a light rectangle which seems to be the background for the login dialogue, but the input field to enter the password and the other controls are not drawn yet. It seems that the freeze is now taking place a little later.

I also tried a kernel from 

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc4-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc4-maverick/)

(they are compiled with Ubuntu config, but without their patches), if I boot with this kernel, the FGLRX driver get's disabled, and if I ask the computer to turn into stand-by, it just switches off the screen light, and if I move the mouse, the light turns on again and I see the login dialogue, the computer simply stays on.

Bernhard

---

### Post by SriNarayanan on 2010-10-20
**Freese - blinking caps and scroll lock - acpi**  			 			 			 		   		 		 		Sony Vaio EB 16 FG - running ubuntu 10.10  froze while resuming from dimmed screen with blinking scroll lock and  caps log LED.

The scenario was this :-
I just downloaded the acpi using synaptic package manager.
Then installed laptop mode tool using synaptic.

*cat* /proc/sys/vm/laptop_mode
0

Means its not yet enabled.

But decided to remove it .(read  drive spin up and down is not good for HDD)

Had left the laptop for some time , it dimmed screen . When I resumed it froze.
No mouse movement.only blinking caps and scroll.

Just wondering if acpi is the culprit,since haven't seen this behaviour before and it happened after removing  laptop mode tools

It happened again , this time while playing a movie on totum .
I was running top on another terminal just to see cpu usage .

Now remove acpi , let me see if it happens again after the removal.

Also I am using a USB mouse , may be it has something to do ?

---

