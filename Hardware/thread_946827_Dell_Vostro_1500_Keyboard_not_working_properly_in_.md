---
title: "Dell Vostro 1500 Keyboard not working properly in Ubuntu 8.10"
date: 2008-10-13
forum: Hardware
---

### Post by amituttam82@gmail.com on 2008-10-13
Dear Friends,

I upgraded from Ubuntu 8.04 to 8.10 and have had a few problems as you might imagine. I have solved most of them but can't solve this one. I hope you have some thoughts.

I have a Dell Vostro 1500 with a replacement keyboard because the original had a key pop out. Now the replacement was from Dell warranty and is working great on Vista and on 8.04 but when I upgraded to 8.10 it has a weird layout that I can't seem to change. Keys on the right end of the keyboard including the arrow keys, Delete button etc. are not working and map to completely different points. I have the layout applet on my panel running and have tried almost all the different dell layouts, generic pc 101 layout etc. Nothing works and nothing seems to change either.

Also in 8.04 all the media keys were working properly. So sound and play and stop etc. were working from the get go. No more with 8.10. I tried keytouch but its too complicated to figure out all that. Why can't it just work like it did with 8.04!:confused:

Now on Ubuntu 8.04 the keyboard was working great from installation, no problems. I upgraded to 8.10 using the upgrade in the package manager. What do I do? Its frustrating cause I have solved my nvidia graphics card problem and finally figured out how to restore my desktop manager and get compiz-fusion working as well as restoring my old settings, only to be hung up to dry because of my keyboard. My sys reqs. are given below.

Dell Vostro 1500
Ubuntu 8.10 -> upgrade from inside 8.04(package manager upgrade **not** clean install)
Keyboard currently set at USA, Dell Inspiron Laptop.
1GB RAM (plan to upgrade to 2GB when funds avail.)
Ubuntu running out of USB 2.0 external IDE Hard Drive in enclosure.

Thanks for anything really!

---

### Post by amituttam82@gmail.com on 2008-10-14
Ok so there is a workaround to this bug. Please check out [https://answers.launchpad.net/ubuntu/+question/47860](https://answers.launchpad.net/ubuntu/+question/47860) For more. Thanks to midnightflash on launchpad. 

Hopefully the powers that be at Ubuntu HQ will get wind of this bug and squash it before it crawls out and frustrates other users. I hear the clock is ticking for a new release!

---

### Post by Ampulse on 2008-11-07
> X.Org Input Devices

The X.Org configuration file (/etc/X11/xorg.conf) still has InputDevice entries for the mouse and keyboard, but they are ignored now because input-hotplug is used. The keyboard settings now come from /etc/default/console-setup; to change them please use sudo dpkg-reconfigure console-setup. After that, HAL and X need to be restarted (e.g., by rebooting your system). 

This helped me!!!

---

