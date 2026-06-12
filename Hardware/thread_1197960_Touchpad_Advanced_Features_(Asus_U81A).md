---
title: "Touchpad Advanced Features (Asus U81A)"
date: 2009-06-26
forum: Hardware
---

### Post by jwburnside on 2009-06-26
Hey everyone, I just purchased a new laptop and the Ubuntu installation went well, but no matter what I try I cannot seem to enable the configuration options for this touchpad.  I have tried many different suggestions from various threads, which usually involve editing the xconf.config file, which usually breaks the touchpad or does nothing.  Here are some specs:

Laptop Manufacturer/Model: Asus U81A
Ubuntu Version: 9.04 Jaunty
Touchpad: Elantech 

I was under the impressions that this type of touchpad can be used with the Synaptic Touchpad driver with a few modifications, but the threads only specify for the eeepc line of Asus, which doesn't seem to work.

I realize this is a pretty new laptop series (I think), so any help would be appreciated.  Let me know if you need more config settings,


hwinfo --mouse
Unique ID: AH6Q.oV6xZUCQFf1
  Hardware Class: mouse
  Model: "ImPS/2 Logitech Wheel Mouse"
  Vendor: 0x0002 
  Device: 0x0005 "ImPS/2 Logitech Wheel Mouse"
  Compatible to: int 0x0210 0x0013
  Device File: /dev/input/mice (/dev/input/mouse1)
  Device Files: /dev/input/mice, /dev/input/mouse1, /dev/input/event8
  Device Number: char 13:63 (char 13:33)
  Driver Info #0:
    Buttons: 3
    Wheels: 1
    XFree86 Protocol: explorerps/2
    GPM Protocol: exps2

JW

---

### Post by ReKast on 2009-08-19
jwburnside,

I have the same model laptop and using Linux Mint (Ubuntu Jaunty Jack 9.04 based) my touchpad automatically has its advance features enabled. Although the touchpad interface is not installed as synaptic, you can still use the three finger and two finger commands. was there something particular you were trying to enable?

also off topic, how is your battery life on this unit, it is claimed to be 7 hours long, I usually get close to 2:45. Do you know how to extend this?

---

### Post by orengolan on 2010-01-25
jwburnside and anybody else with this issue,

There is a problem with Elan touchpad.
I submitted the bug on Launchpad:
[https://bugs.launchpad.net/ubuntu/+s...cs/+bug/512192](https://bugs.launchpad.net/ubuntu/+s...cs/+bug/512192)

Please go there and change the status to 'Confirm' so Ubuntu developers will understand that it's a hardware issue and not something specific to me.
Also mention your hardware.

Thanks you so much!


ReKast,
the problem we all have is we can't configure the touchpad,
for example disabling it or changing it's sensitivity.

---

