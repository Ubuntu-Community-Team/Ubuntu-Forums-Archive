---
title: "ConstantDeceleration for one of two mice"
date: 2010-05-02
forum: Hardware
---

### Post by Edward C on 2010-05-02
Hi,

I have a laptop that I use at home and at work. The mouse at work is fine with the default settings, but to properly use the mouse I have at home it needs a ConstantDeceleration set. Earlier versions of Ubuntu used a HAL .fdi file to configure this option, then came udev rules, and now it seems that the method has changed again for 10.04 and the option must be specified in xorg.conf or an xorg.conf.d file. I'm currently facing two issues:

- Though X acknowledges the configuration option, it has no effect.

- Assuming I can tweak the config to get X to apply the option, I have no idea where to begin to configure it for only one of the two mice I regularly use, as was possible with the HAL and udev methods.

Here's what I've added to my xorg.conf:


Section "InputDevice"
Identifier "Microsoft Wireless Mouse 5000"
Driver "mouse"
Option "ConstantDeceleration" "200"
Option "AutoServerLayout" "true"
EndSection

Section "ServerFlags"
Option "AllowEmptyInput" "false"
EndSection


and here's some of the Xorg.0.log output:


(II) XINPUT: Adding extended input device "Microsoft Wireless Mouse 5000" (type: MOUSE)
(**) Microsoft Wireless Mouse 5000: (accel) keeping acceleration scheme 1
(**) Microsoft Wireless Mouse 5000: (accel) constant deceleration by 200.0
(**) Microsoft Wireless Mouse 5000: (accel) acceleration profile 0
(**) Microsoft Wireless Mouse 5000: (accel) acceleration factor: 2.000
(**) Microsoft Wireless Mouse 5000: (accel) acceleration threshold: 4


I've tried a range of different values for ConstantDeceleration, from my normal setting of 2 up to the ridiculous 200 shown in my pasted examples. Nothing has made the slightest difference.

Any ideas what's wrong here?

And ideas about whether it's possible to target a single mouse with the xorg.conf approach, or will I need to swap config files twice a day?

Thanks,
Ed.

---

### Post by Tyroie on 2010-05-02
I'm very new to Ubuntu, however just before finding your post here, I was just messing with a terminal command called Xinput to customize some mouse settings, and I think you might be able to use that. Sorry in advance if this doesn't actually help, because I'm really not sure.

To get to the terminal, click Applications -> Accessories -> Terminal

Once there, type this command to see all connected mice and keyboards:  xinput list

The mouse you want to mess with should be in that list, and it should tell you its ID number to the right.

Then to view all the properties of that mouse (like the deceleration), type this command, but replace the # with the ID number of your mouse:  xinput list-props #

When I do that, that's when I see the Constant Deceleration option. For me, The ID number for that property is 235, I don't know if it's the same for you.

To actually edit that property, you'll type this command:  xinput set-prop (mouse ID) (deceleration ID) (value)
So for my computer, I type:  xinput set-prop 8 235 2

And that seems to work as far as I can tell, the mouse control should update instantly. However, this special setting will go away when you reboot. I wouldn't be surprised if there's a smarter way to do it, but I set it up to run that xinput command whenever Ubuntu starts up.

To do that, click System -> Preferences -> Startup Applications
Click Add.  Name this anything (like mouse settings)
In the Command spot, type in this, except change the numbers for what worked for you:  /usr/bin/xinput set-prop 8 235 2

Though... If both the mouse at work and the mouse at home have the same ID number, automatically running xinput when you boot would be bad... Maybe one option there would be to create a desktop icon for the xinput command (right click desktop, create launcher) so you can just click that when you boot up the computer at home.

---

### Post by Edward C on 2010-05-02
Thanks Tyroie, that's equivalent to the work-around I'm using at the moment:

xinput set-prop 9 "Device Accel Constant Deceleration" 2

It works, but running that command in a terminal twice a day seems like a bit of a hack compared to the completely automated methods (HAL .fdi and udev rule files) that used to be available.

---

### Post by dtfinch on 2010-05-02
Thanks for the workaround.

Looks like you can substitute the device name too:
xinput set-prop "PS/2+USB Mouse" "Device Accel Constant Deceleration" 2

---

