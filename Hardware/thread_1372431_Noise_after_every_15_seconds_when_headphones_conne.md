---
title: "Noise after every 15 seconds when headphones connected"
date: 2010-01-04
forum: Hardware
---

### Post by whistl3r on 2010-01-04
Every since i upgraded to karmic, whenever i connect headphones to my laptop I get the annoying tap noise after every 15 seconds. I comes both from the speakers and the headphones. 

In the beginning i tried to ignore it but now its driving me crazy. Without the headphones, everything works fine.

My laptop is a HP dv6000, its using the snd-hda-intel driver.

---

### Post by lavinog on 2010-01-04
I had a simmilar problem with my desktop.
It turned out to be a new powersave feature for the sound card.
You can try this to see:

Press alt-f2
```

gksudo gedit /etc/modprobe.d/alsa-base.conf

```

find a line that looks like this: (it was at the end of the file for me)
```

options snd-hda-intel power_save=3600 power_save_controller=N

```
add a # in front to comment it out like this:
```
#options snd-hda-intel power_save=3600 power_save_controller=N

```
save and reboot.
See if that helps.
You can undo the changes by removing the # if it didn't help.

---

