---
title: "Logitech MX on 7.10 RC?"
date: 2007-10-13
forum: Hardware &amp; Laptops
---

### Post by jfbaro on 2007-10-13
Hi,

I intend to buy a Logitech MX revolution mouse to use in conjuction with my laptop. If I do, would Ubuntu allow me to use all its functions? If not, which other high-end mouse is more suitable to Linux?


[http://www.logitech.com/index.cfm/mice_pointers/mice/devices/130&cl=us,en]("http://www.logitech.com/index.cfm/mice_pointers/mice/devices/130&cl=us,en")

Thanks guys!!

---

### Post by dasunst3r on 2007-10-13
I have a Logitech MX 610, and it was hell and high water to get most of its functionality working.  To be honest with you, don't bother with anything more than a simple scrolling mouse with back/forward buttons.

---

### Post by jfbaro on 2007-10-13
Thanks.

That's a shame though as I think its functionalities great! Would you suggest any other mouse or any standard one would be enough? I use the computer for long hours every day...

Cheers

---

### Post by Depressed Man on 2007-10-13
I have that mouse for my laptop..it worked under Feisty with BTNX. Haven't tried in Gutsy yet.. (but right now only the basics work..as in the three main buttons on any mouse).

---

### Post by smrsmrf47 on 2007-10-18
I have my 'Search' button on my MX Revolution mapped to Ctrl+W so I can close tabs in Firefox. (I'm still running Kubuntu 7.04 btw). These are the steps I followed:

Install hotkeys and xvkbd.
Create a MyHotkeys.conf file at /usr/share/hotkeys/MyHotkeys.conf .

The keycode for the MX Revolution's Seach button is 122, and is interpreted as a keyboard event (even though it comes from the mouse). So, add the following to  /usr/share/hotkeys/MyHotkeys.def :
```
<userdef keycode="122" command="xvkbd -xsendevent -text \Cw"></userdef>
```
(The X Virtual Keyboard sends the Ctrl+W (\Cw) event to the active window.)

Edit /etc/hotkeys.conf so that:
```
Kbd=MyHotkeys
```

Assuming you have KDE, create a script that runs the command: 
```
hotkeys --no-splash --osd=off
```
and save it in ~/.kde/Autostart/
I don't know what the corresponding instructions for Gnome are but I'm sure you can find it on these forums.

---

