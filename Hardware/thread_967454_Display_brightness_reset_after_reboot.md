---
title: "Display brightness reset after reboot"
date: 2008-11-02
forum: Hardware
---

### Post by jeenuv on 2008-11-02
I recently upgraded to Ibex from Heron (Dell Inspiron 6400). When Ibex boots up, the LCD brightness is reset to the maximum, despite me setting to my custom level prior to the reboot. Hence I've to adjust it every time I reboot. Any clues why it does this?

Also the keys used to control display brightness (Fn + Up/Down) doesn't work smoothly. A single press of the key combination adjusts the brightness to more than one levels; i.e. instead of moving to the next/previous level, it jumps 2 or 3 levels form the current level. 

For the sake of easiness and consistency, I'm working this around by writing to file /proc/acpi/video/VID/LCD/brightness via. a script so that I can set it to my desired level in a single shot.

---

### Post by lett on 2008-11-17
I've noticed the same on mine laptop (acer travelmate 2423). Fresh install of Ibex. I will try to add this line:

echo -n 50 > /proc/acpi/video/VGA/LCD/brightness

at the end of /etc/rc.local file.

---

### Post by jeenuv on 2008-11-17
Actually I have a script just to do that. What's annoying me is that Ubuntu doesn't respect my settings for brightness. The same happens for network-applet - I disable wireless networking when I use ethernet port; but it's back up enabled on reboot! Again there are some other annoyances like balloons appearing in wrong place and tray icons appearing on the desktop corners instead of the task-bar. I suspect my upgrade wasn't quite successful from Hardy Heron to Intrepid Ibex

---

### Post by lett on 2008-11-17
Do you mean it (your script) does not change brightness after restart?

---

### Post by jeenuv on 2008-11-18
My script does change the display brightness; but I haven't put in /etc/rc.local. But no matter what the brightness is set to, it's reset to maximum on boot up. But I guess that shouldn't be the case

---

### Post by lett on 2008-11-19
Well, maybe you are right. It is not a big deal to change brightness after every reboot, it might be only annoyingl. Do you know what module controls LCD brightness? I suppose it should be connected somehow with acpi.

---

### Post by jeenuv on 2008-11-20
I did try putting the script in /etc/rc.local but that didn't seem to have any effect; so I think I better do it manually every time I reboot -- bit pity though.

And, sorry, I've no idea what controls the brightness.

---

### Post by alecz20 on 2009-01-27
I have the same problem on an Acer laptop.

The brightness worked well in 7.10 and 8.04

In 8.10 the intensity is set to 100% after reboot. When I try to dim it down, the slider is already at zero intensity, but at least it dims.

This surely is annoying; at least I try to reboot as rarely as possible.

Apparently it's an old bug, that has been on and off:
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/35223](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/35223)

---

### Post by Bosconian on 2009-02-01
Anyone got a fix for this? My Acer laptop does the same thing. It is always back at maximum after a reboot. It is annoying because sometimes I don't realise until my eyes are burning.

---

### Post by alecz20 on 2009-02-19
the only "fix" right now is running Hardy instead of Intrepid. :(

---

