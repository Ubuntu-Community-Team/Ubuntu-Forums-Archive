---
title: "Lingering HP clickpad problems"
date: 2010-10-23
forum: Hardware
---

### Post by HP dv4 on 2010-10-23
I have a new HP dm4 that I recently installed Ubuntu 10.10 on. The laptop has has an all-in-one clickpad that seems like it's trying to ape a macbook. Since it's software based it would not initially right click. I got that problem fixed fom a previous thread:
Re: HP Mini 210 touchpad right click not working
To get the trackpad working correctly you need to use the terminal and enter in the below commands. Make sure you press enter after each command:

Code:
sudo su
Code:
echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
Code:
reboot

Once the computer reboots your trackpad will be able to do left click and drag and right clicking.
Last edited by Sabot; February 12th, 2010 at 01:09 PM..
______________________________________________________
It did what it was suppose to do, but it removed the touchpad menu from the mouse options so that I can't disable tap-to-click or have any way to scroll with the clickpad.
Any help is appreciated.

---

