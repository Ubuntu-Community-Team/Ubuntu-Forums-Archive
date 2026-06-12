---
title: "Can't disable system beep in Feisty"
date: 2007-05-04
forum: Hardware &amp; Laptops
---

### Post by BoyMike on 2007-05-04
Hi,
I'm having some trouble with disabling my pc speaker.
I have been following some guides here on this fourm but to no avail.
I have tried adding:
```
modprobe -r pcspkr
```
To /etc/rc.local

And:
```
blacklist pcspkr
```
To /etc/modprobe.d/blacklist

And running:
```
sudo rmmod pcspkr
```
Which gives the following error:
```
ERROR: Module pcspkr does not exist in /proc/modules
```
From terminal...

Hopefully there is something else i can do to get this annoying sound turned off.
I'm running Feisty on a Dell 6400 with X1400 graphics, if it's to any use.

Any thoughts are appreciated!
/Mike

---

### Post by jack1254 on 2007-05-04
It isn't quite disabling, but how about just turning down the volume?

Using ALSA:
```
amixer set "PC Speaker" 0
```

If for some reason your PC Speaker isn't called "PC Speaker", run
```
amixer scontrols
```
to get a list of options

---

### Post by biffta on 2007-05-04
If it's actually the "system beep" you're trying to mute you can just do it from

System->Preferences->Sound->System beep

---

### Post by teasum on 2007-05-04
Just to add the the original post, I am having this trouble as well on my Dell Insprion 8600.  I have the visual beep enabled, but for some reason, in some circumstances, the beep seems to reappear.

Also, I don't think the PC speaker volume has anything to do with the system beep... though I could be wrong.  I'd be interested to hear solutions, or to know if this is a reported bug somewhere.

---

### Post by Toadmund on 2007-05-04
1) Buy or pilfer can of compressed air.
2) Blast the dust off every component including inside power supply.
3) wait for beep, if no beep, congratulations, it was just dust buildup heating up and making your computer  less efficient.
4) more beeps? 1, 2, 3 didn't help obviously.

(personal experience)

I would call a computer an expensive air cleaner.

---

### Post by BoyMike on 2007-05-05
Well it would seem that I have found something that works, for me at least.
Running:
```
sudo modprobe -r pcspkr
```
Does the trick for the running session!

However I un ticked the system beep form the sounds option panel before reboot, behold no system beep. The weird thing about the unticking is that it didn't work the previous times...

Well anyway the beeping is gone. For now.
/Mike

---

### Post by wt8008 on 2007-05-06
Blacklisting the pcspkr module in /etc/modprobe.d/blacklist does not take effect until you reboot, so you had to run a sudo modprobe -r pcspkr to remove it from your running system. 

By blacklisting the pcspkr module is the way to completely disable the module. I also run a Dell laptop, and I only unchecked the system beep option in Gnome, but when I switched to the full screen shell with <CTRL+ALT+F1> the beep came right back. I was also in a classroom environment, so everyone started to look at me, but blacklisting and a reboot fixed that issue.

---

