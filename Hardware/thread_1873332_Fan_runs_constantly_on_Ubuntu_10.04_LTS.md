---
title: "Fan runs constantly on Ubuntu 10.04 LTS"
date: 2011-11-01
forum: Hardware
---

### Post by tuxt on 2011-11-01
Hi 

Am hoping that someone might be able to help me.

I am running Ubuntu 10.04 LTS, on a Toshiba Satellite C660D-128.

Everything works fine, except one thing, the fan runs constantly, no matter what I do.

Feels that this isn´t right. 

All the help is much appreciated

---

### Post by shubham1 on 2011-11-01
> **tuxt said:**
> Hi 

Am hoping that someone might be able to help me.

I am running Ubuntu 10.04 LTS, on a Toshiba Satellite C660D-128.

Everything works fine, except one thing, the fan runs constantly, no matter what I do.

Feels that this isn´t right. 

All the help is much appreciated
did the fans run on another oses too

---

### Post by 2F4U on 2011-11-01
Is this an older laptop? If yes it may be worth to open the case an clean the inside from dust.
Otherwise, did you check whether there is something heavy running in the background?

---

### Post by tuxt on 2011-11-01
Hi

I have tried other Ubuntu and Linux distro, but never encounter this problem before.

I purchased the laptop early January, 2010, will open the case and check whether it needs to be cleaned, thanks.

Have used the program TOP, and the program that is used most of is only around 2%

I found a thread, similar to my problem. However, it is quite old

[http://ubuntuforums.org/showthread.php?t=1059548](http://ubuntuforums.org/showthread.php?t=1059548)

Many thanks for all your help

Ubuntu is the best!

---

### Post by 2F4U on 2011-11-01
What graphics card is in the machine and what driver do you use? If it is an ATI or nVidia card, you would have an option to install the proprietary drivers, if you are not already using them. The power management of the proprietary drivers is better than that of the open source drivers, in particular if you are using desktop effects.

---

### Post by tuxt on 2011-11-01
Hi again

Here is the output from lspci -v 

01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
	Subsystem: Toshiba America Info Systems Device ffb0
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 9000 [size=256]
	Memory at cfdf0000 (32-bit, non-prefetchable) [size=64K]
	Memory at cfe00000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>
	Kernel driver in use: radeon
	Kernel modules: radeon


Am not using the proprietary drivers at the moment, 
but will install them right away, 
thanks so much for all the help

---

### Post by tuxt on 2011-11-01
Thanks so much for all your help. 

Installing the proprietary drivers seemed to have solved the problem. 

Am attaching a screenshot of my CPU usage, please feel free to comment if something seems wrong.

---

