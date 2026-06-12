---
title: "Disabling non-synaptics trackpad"
date: 2008-03-07
forum: Hardware &amp; Laptops
---

### Post by dfstein on 2008-03-07
**This post could be related to an Ubuntu bug filed at**: 123775 [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I recently installed Gutsy on an Averatec 1100 laptop.  Had a lot of success solving other problems by googling, but I think I've finally struck out on this one so maybe someone here can help.

Basically, I want to disable my trackpad whenever a mouse is plugged in.  I'm open to nice options but at this point I'd be happy with just a macro or something to run whenever I plug in my external mouse. 

Unfortunately, I think I'm running into this bug:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/123775](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/123775)
 
cat /proc/bus/input/devices shows my trackpad like this:

I: Bus=0011 Vendor=0002 Product=0005 Version=0063
N: Name="ImPS/2 Logitech Wheel Mouse"
P: Phys=isa0060/serio4/input0
S: Sysfs=/class/input/input2
U: Uniq=
H: Handlers=mouse1 event2 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

and qsynaptics complains that the synaptics driver isn't running when it is.  I've tried all sorts of xorg.conf stuff to no success.  

Sure it would be nice to just change the double tap rate, or adjust the sensitivity, but at this point I'd be happy if I could just turn the whole thing off.  I keep bumping it with my palms when I type making it impossible to write anything very long without getting frustrated.  But I also want to be able to turn it back on again with a keystroke or two for those rare occasions when I just take my laptop out for a second to check something and don't want to fumble with the mouse.  

This is my first linux install in 8 years ago, and I must say its come a long way.  Its a downright pleasure to use in most ways, fast, stable, and east.  It even recognized my wireless card where XP wouldn't.  If I can just disable this silly trackpad on demand  I'm going to start using it full time.  

thanks in advance for any ideas.
-D

---

