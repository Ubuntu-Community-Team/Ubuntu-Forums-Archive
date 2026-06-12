---
title: "Laptop Brightness Problem - Changes After Return From Idle"
date: 2009-10-27
forum: Hardware
---

### Post by Xebek on 2009-10-27
Ok, now I know there have been similar problems posted around either here or in general around the internet but none of them seem to really have a good answer, so I figured I would kind of re-state my issue I have here.
 
I have recently installed ubuntu, 9.04 or so I believe. It is on a Asus Eee PC 1005HA. Now right after the install, it seemed that the brightness controls worked somewhat. I was able to in general adjsut the brightness with function keys. However my problem comes when the computer idles. 
 
If I set my brightness down to 20 percent, or really anything, and then don't use the computer long enough for it to auto dim itself due to inactivity (To save battery power and such), whenever I use it again, move the cursor, hit a button, the screen will jump to 100 percent brightness, not what it was left off at. In other words, the brightness will go to max after the idle dim, not the previous setting.
 
Can anyone please tell me how to fix this? It is very annoying, espeically when in a classroom that is dark and I need the screen slightly dimmer to not annoy people, having it jump up just becasue of the idle dim is VERY annoying and may cause me to stop using the OS altogether, which I really don't want.

---

### Post by georgeslurpy on 2009-11-04
I am have the same problem. Mine isn't a netbook, but an Asus UL30A-A2 laptop. Any help would be appreciated. Thanks.

---

### Post by boom2k1 on 2009-11-09
I also have an Asus UL30A and I am having the same problem.

I am quite disturbed by the screen brightness bug. On battery, idling causes the laptop to change screen brightness. Changing the setting from power management to prevent dimming while idling apparently doesn't work. Because I worked under low light environment, I set brightness to really low. When idling, it actually changes my brightness up!

Moreover, there also seems to be another problem moving my cursor after "dimming". The expected behaviour of the laptop should be to make the laptop to return to previous setting. However, it seems to reset it to something else (probably to the default setting under power management)!

---

### Post by boom2k1 on 2009-12-09
I think the problem kind of went away for me.

Can anybody confirm whether this procedure can fix it?

Uninstall gnome-power-manager. (i know it sounds scary)

sudo apt-get remove gnome-power-manager 
in the terminal.

It will affect some other things, but it will just be temporary.
then maybe do a reboot

and then do

sudo apt-get install gnome-power-manager

to reinstall it back!

See if it works. I am now thinking maybe this procedure would over-ride the default setting.

---

### Post by jollyjollyroger on 2009-12-13
Have dell studio 15.

Would love my brightness to just stay where i left it.

Being a laptop user i have a battery and also locations that require certain lighting levels.

It would be very useful if my brightness had some form of memory.

Please and thankyou.

---

### Post by vortex58 on 2009-12-30
I found an alternative for setting the brightness. Just add the "Brightness applet" to your panel. The value set by this will stay.

Steps:

- Right click a panel and select "Add to Panel".
- Select the "Brightness applet".

---

### Post by jollyjollyroger on 2009-12-31
> **vortex58 said:**
> I found an alternative for setting the brightness. Just add the "Brightness applet" to your panel. The value set by this will stay.

Steps:

- Right click a panel and select "Add to Panel".
- Select the "Brightness applet".

The aforementioned applet has no obvious effect on my brightness, despite manipulation of the slider...
 Am i missing something?

---

### Post by louisdl on 2009-12-31
My problem is that I cannot adjust the brightness at all. It stays at the max at all times. The other function keys work. I am using Ubuntu 9.10 on an HP-G60-230US laptop. I have no problem adjusting the brightness on my Dell Inspiron B130 running Ubuntu 9.04.

---

