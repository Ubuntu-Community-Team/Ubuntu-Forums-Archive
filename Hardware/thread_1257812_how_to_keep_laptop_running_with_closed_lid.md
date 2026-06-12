---
title: "how to keep laptop running with closed lid"
date: 2009-09-04
forum: Hardware
---

### Post by gukarma on 2009-09-04
hi there,

i have an acer 5672 connected to a 24" samsung monitor. i would like to be able to close the laptop lid and store it under my desk while using the external monitor. right now, when i close the lid the system goes into standby.

thanks,

gukarma

---

### Post by sv1cdn on 2009-09-04
System -> Preferences -> Power management and check appropriate action on AC and battery power.

---

### Post by zachth3 on 2009-09-04
I also want to know the answer of this question. so please tell me.

---

### Post by Rich_B_uk on 2009-09-04
Read above.

---

### Post by theclerm on 2009-10-30
Hi,

I can't get my computer to keep running when the lid is closed (and my laptop is connected to an external dispplay). In the power management options, the only settings available are: blank screen; Suspend; Hibernate; Shut down. There is no "Do Nothing" option.

Any idea what I could do?

Thanks

---

### Post by rich97 on 2009-10-30
There is a (very annoying) regression in Karmic described here:

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/416236]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/416236")

[I][COLOR="Red"]The potential work around described in that thread does not work...

I'm really no expert with Ubuntu, I only have a base knowledge of how the system works. If I find a fix I will post it here. Would really appreciate some expert input. :([/COLOR][/I]

**Edit:**

OK apparently the fix does work and I was just being a tool.

Go to terminal and enter:
```
sudo gconf-editor
```

Using the file browser navigate to:
```
/apps/gnome-power-manager/buttons
```

Select edit the keys "lib_ac" and if you want "lib_battery" and chenge their value to "nothing" (no quotes). And close the editor.

Then select:
System > Power Management

Et voila! There should be an option to "do nothing" on lid close. :)

---

