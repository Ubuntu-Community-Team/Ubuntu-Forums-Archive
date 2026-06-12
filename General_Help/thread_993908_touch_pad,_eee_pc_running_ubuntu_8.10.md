---
title: "touch pad, eee pc running ubuntu 8.10"
date: 2008-11-26
forum: General Help
---

### Post by alec868 on 2008-11-26
i recently installed ubuntu 8.10 on an eee pc 900. i9m quite haooy with it, with the exception of the drag and drop on my touch pad. when im, espically, on the web the mouse is set to select text when i use two fingers, and its maddening. every page i go to im auto selecting text all i want to do is turn it off. can anyone help?

---

### Post by silkstone on 2008-11-26
I'm running Ubuntu-eee 8.04.1 on an eee PC 901, so what I say here may not apply 100% to you, but you need to install the Gsynaptics touchpad control...

**How to get Gsynaptics working to control Touchpad...**

Install gsynaptics (elantech version) from synaptic. Then...

gksudo gedit /etc/X11/xorg.conf

Add the following to the Synaptics Touchpad section...

Option "SHMConfig" "true"

Save and close.

Then create a file called psmouse in /etc/modprobe.d ...

gksudo gedit /etc/modprobe.d/psmouse

Type the following into this file...

options psmouse elantech=1

Save and close, then reboot.

You should now have a Touchpad option under Preferences which allows you to control many functions. There will also be a touchpad tab under the Mouse preferences, and it's a good idea to ensure that the options in both don't conflict.

Hope that helps.

---

