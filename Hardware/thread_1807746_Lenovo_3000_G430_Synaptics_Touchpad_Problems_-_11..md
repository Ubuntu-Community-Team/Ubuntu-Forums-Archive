---
title: "Lenovo 3000 G430 Synaptics Touchpad Problems - 11.04"
date: 2011-07-19
forum: Hardware
---

### Post by ddrake on 2011-07-19
Hi

 I have successfully installed Ubuntu 11.04 on Lenovo 3000 G430 laptop. While 'xinput list'  details that the virtual core pointer has the touchpad:
[FONT="Courier New"]SynPS/2 Synaptics Touchpad id=13 [slave pointer (2)][/FONT]

my touchpad refuses to respond and I have to use an external mouse.

I do not want to use the external mouse.

How can I get the touchpad to be activated and be usable?

thanks in advance
DDrake

---

### Post by ddrake on 2011-07-21
Thanks to Andrew (Launchpad) the solution is:

On booting up, first press Fn+F8  twice to activate the touchpad.

Source:
[http://www.linlap.com/wiki/lenovo+3000+g430](http://www.linlap.com/wiki/lenovo+3000+g430)

it works smooth.

What did NOT work (which I had gathered through various forum pages) are:
a) installation of gsynaptics - this is deprecated now
b) doing the following:
    " sudo echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe"  - this hung up the machine and I had undo
c) removing the battery and power for several minutes and then rebooting it.


thanks to all
:)

---

