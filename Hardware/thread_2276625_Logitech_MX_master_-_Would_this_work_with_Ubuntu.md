---
title: "Logitech MX master - Would this work with Ubuntu?"
date: 2015-05-04
forum: Hardware
---

### Post by madu on 2015-05-04
I would like to buy the Logitech MX Master but would like to know if I'd be able to use its features on Ubuntu.
If somebody has gotten this to work with Ubuntu could you please share some information and also which BT receiver was used.
Thank you very much.

---

### Post by linux-0 on 2015-06-20
Yes the wireless [COLOR=#000000]MX Master[/COLOR] run but you need to install solaar if you use the Unifying receiver wich I use!
If you need BT I don't know...

Terminal:
sudo add-apt-repository ppa:daniel.pavel/solaar
sudo apt-get update
sudo apt-get install solaar

---

### Post by JB19 on 2015-06-27
> **linux-0 said:**
> Yes the wireless [COLOR=#000000]MX Master[/COLOR] run but you need to install solaar if you use the Unifying receiver wich I use!
If you need BT I don't know...

Terminal:
sudo add-apt-repository ppa:daniel.pavel/solaar
sudo apt-get update
sudo apt-get install solaar

Thank You! Works like a charm.

---

### Post by efflandt on 2015-06-28
One "feature" of MX Master which is great for general computer use, but can be a bit annoying when gaming is that there is a button on the foot below your thumb that does Ctrl+Alt+Tab which switches to a different window, or to the desktop. To disable that in regular Ubuntu with Unity and Compiz, install compizconfig-settings-manager if you do not have that, and under **Ubuntu Unity Plugin** > **Switcher** disable "Key to flip through windows in the Switcher" and since it still picks up the Alt+Tab, change "Key to start the Switcher for all viewports" to something like "<Control><Alt>Home". Then you should still be able to get to the Switcher if a full screen program hangs for some reason.

Other than that Steam sees the side scroll wheel or side buttons as mouse4 (scroll up or lower button) and mouse5 (scroll down or upper button).

The **Power Statistics** app in Ubuntu does not show battery level of MX Master, but it has 3 LEDs on the side to indicate battery level whenever you turn it on or first move it after being inactive for a while, so you can tell when you need to charge it.

---

