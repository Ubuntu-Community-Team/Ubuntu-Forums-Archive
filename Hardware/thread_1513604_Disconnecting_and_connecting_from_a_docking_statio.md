---
title: "Disconnecting and connecting from a docking station?"
date: 2010-06-19
forum: Hardware
---

### Post by qbertsoul on 2010-06-19
Hey there,

I have a Dell Latitude D630 running dual-boot Windows XP and Ubuntu 10.04 with an NVIDIA graphics card/driver.

I have my laptop connected to a docking station which connects a 17" monitor to the computer. I currently have it set up on Twinview with the external monitor as my primary screen.

Now, when I DISCONNECT the laptop from the docking station, Windows XP will automatically change the settings to make the laptop screen the primary screen.

In Ubuntu, this is not the case, and it continues to act like it's still in Twinview (mouse cursor will even still be able to go far off screen).

Is there any way to get the Windows XP like setting where it uses Twinview when a monitor is connected, but doesn't otherwise?

Adam

---

### Post by klap-in on 2010-06-30
I look also for something that automatically switch on and off screens that are plugged in. 
The only way for now i see is manual enable and disable my second screen in the Nvidia-Server Settings window. 

A first view on 'nvidia-settings --h' seems showing options to run it without GUI, so maybe this can be usefull to define two config files which you call and set by nvidia-settings each by a different shortcut. I will try this, but not this month (too busy).

---

