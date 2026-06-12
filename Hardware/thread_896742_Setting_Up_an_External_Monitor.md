---
title: "Setting Up an External Monitor?"
date: 2008-08-21
forum: Hardware
---

### Post by Rainagul on 2008-08-21
Hi.
Ive had ubuntu for a while now and really enjoying it. ]
However i would like to use my 22inch screen instead of using my laptop.
What would be the steps to go around getting it to work?
I ask this because when i restarted my computer and plugged in my monitor, it didnt show on the Monitor just my laptop.

Thanks :)

---

### Post by bankg3 on 2008-08-21
If you are using hardy heron (8.04) just go to the screen resolution app in the menu (under system -> preferences) and you can move your two connected monitors around (external and laptop), mirror your output to both of them, or just turn one of them off (laptop)

---

### Post by Rainagul on 2008-08-21
Im using Ubuntu.

And when connect my monitor and and look in screen resolution. I can't see the new screen, so thats my problem...

---

### Post by pschandra on 2008-08-24
> **Rainagul said:**
> Im using Ubuntu.

And when connect my monitor and and look in screen resolution. I can't see the new screen, so thats my problem...

Same problem for me.
My laptop is Thinkpad T61.
I just updated to Ubuntu 8.04. But it is showing [COLOR="Red"]laptop screen[/COLOR] instead of [COLOR="Red"]External Dell screen[/COLOR], which is attached to my Dock.

Please help.

Thanks,
Sathish

---

### Post by bankg3 on 2008-08-25
In Ubuntu 8.04 the screen resolution application shows both monitors, but an initial (default) setup puts both monitors in the same spot, so basically one of your monitors is covering the other one.  Just grab the monitor and move it with the mouse and you should see your other monitor underneath it.

---

### Post by irw on 2008-08-25
I've been looking into this recently.

If I book my laptop with an external monitor attached, it shows the initial boot screens, but when gdm starts the external monitor goes blank and complains of no signal.

This suggests to me that the xorg.conf file may need tweaking.

---

### Post by bankg3 on 2008-08-25
> **pschandra said:**
> Same problem for me.
My laptop is Thinkpad T61.
I just updated to Ubuntu 8.04. But it is showing [COLOR="Red"]laptop screen[/COLOR] instead of [COLOR="Red"]External Dell screen[/COLOR], which is attached to my Dock.

Please help.

Thanks,
Sathish

Look here for dell docks and ext. monitor support, it might help a little bit. [http://ubuntuforums.org/showthread.php?t=879045&highlight=dell+dock+external+monitor]("http://ubuntuforums.org/showthread.php?t=879045&highlight=dell+dock+external+monitor")

> **irw said:**
> I've been looking into this recently.

If I book my laptop with an external monitor attached, it shows the initial boot screens, but when gdm starts the external monitor goes blank and complains of no signal.

This suggests to me that the xorg.conf file may need tweaking.

have you tried the screen resolution application? If so and you still have this problem post your xorg.conf and I'll see if there is anything that stands out to me ... also post a hardware list with this command
```
lspci
```
and also
```
lshw
```

Thanks!

---

### Post by caco on 2008-09-04
Plugging the External VGA device should usually activate that device.
You can then switch between LCD, LCD + VGA, VGA by pressing Fn+F5 or such key combination on your laptop. Though be prepared most of the time some portion of the screen on the VGA device plugged in would be cut off.
[I]
PS: backup your xorg.conf that is sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup[/I]
I got some workarounds from the net/forums which involves editing the xorg.conf, especially the monitor section, part of mine is shown below

Section "Monitor"
	Identifier	"Laptop Monitor"
	Option		"DDC"	"no"    #this you need to add
	Option		"DPMS"	"true"  #this you need to add
	DisplaySize	338 211         #these values are from xdpyinfo???
	Option		"Monitor-LVDS" "Laptop Monitor"
EndSection

???-You need to run 'xdpyinfo | grep dimension' which would give you an output similar to   dimensions:    1280x800 pixels (**338**x**211** millimeters)

All that is remaining is to save the modified xorg.conf and log out then log back in.
Plug the VGA device in, Start the Screen Resolution Application, click Detect Displays, drag the initial display(ie Laptop) away for the second (VGA or Unknown), apply your preferred settings (clone screen, left of LCD,resolution,etc)
That's all ... hope this helps

---

### Post by caco on 2008-09-04
Another snag is that though this works for me, even with projectors for business meetings... I seem to have either lost the functionality of Fn+F5 on my toshiba laptop

---

