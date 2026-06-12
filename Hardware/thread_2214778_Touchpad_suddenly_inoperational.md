---
title: "Touchpad suddenly inoperational"
date: 2014-04-03
forum: Hardware
---

### Post by rhelmot on 2014-04-03
I've been using lubuntu 13.10 on my laptop (Toshiba Satellite P75-A7200) for several months now, and everything has been fine (well not everything, but not the point here), but a few nights ago I was furiously messing with networking settings on a deadline, and somehow, one of the times I rebooted, the touchpad suddenly stopped responding. I just plugged in a mouse and carried on, thinking I could fix it later, but now I'm kind of stuck.

Symptoms are that there is absolutely no response from the touchpad. No motion, no clicking, no tapping, no scrolling. USB mouse works, though.

Both [FONT=courier new][COLOR=#333333]cat /proc/bus/input/devices[/COLOR][/FONT][COLOR=#333333] and [FONT=courier new]xinput list[/FONT] detect a [/COLOR]SynPS/2 Synaptics TouchPad.

[FONT=courier new]synclient | grep Touchpad[/FONT] returns TouchpadOff = 2, but setting it to 0 or 1 has no effect.

[FONT=courier new]xev[/FONT] sees no mouse events.

I'm not particularly sure how to proceed debugging this, but I would appreciate being able to use my touchpad again!

---

### Post by varunendra on 2014-04-05
During your attempts to fix the wireless, did you blacklist any drivers? Which ones if you did?

If not, try reinstalling the synaptics driver -
```
sudo apt-get install --reinstall xserver-xorg-input-synaptics
```
You may have to reboot for the driver to take effect.

If this doesn't help, please post the outputs of -
```
xinput
synclient
lsmod
dpkg -l | grep synaptics
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by tgalati4 on 2014-04-05
Take a toothpick and gently clean around the edges.  The BIOS will shut off the touchpad if it puts out extraneous signals.  Most computers detect when you are in "furious" mode and start to fail randomly.

Check your log files for error messages:

```
less /var/log/Xorg.0.log
```

Check the BIOS for a touchpad setting:  "Turn off while typing".

---

### Post by rhelmot on 2014-04-08
Reinstalling the drivers didn't work. And no, I didn't intentionally disable any drivers.

Here's all the program outputs you wanted, plus Xorg.0.log: [http://andrewdutcher.com/helium/mouseerror/](http://andrewdutcher.com/helium/mouseerror/)

And I couldn't find any BIOS settings relevant to my touchpad.

---

### Post by tjqt06 on 2014-04-09
hello, I don't know where to post and I hope I'm in the right track. Anyway, I have the same problem encountered. I try to install the synaptic and the error displays as

> Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 xserver-xorg-input-synaptics : Depends: xorg-input-abi-16
                                Depends: xserver-xorg-core (>= 2:1.11.99.901)
E: Unable to correct problems, you have held broken packages.




can you help me to solve the issue on touchpad. I am using Asus X450L Ubuntu 12.04 x64. Thank you.

---

