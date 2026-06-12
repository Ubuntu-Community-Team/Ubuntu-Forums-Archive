---
title: "When an ALPS touchpad doesn't use Synpatics driver and therefore doesn't work"
date: 2011-05-23
forum: Hardware
---

### Post by Llewlyn on 2011-05-23
Hi guys,

I am trying to fix my touchpad on a 11.04 Xubuntu. I have seen many threads on this topic but, up to my knowledge, this specific issue hasn't been dealt yet.

My touchpad is detected as an ALPS GlidePoint and is actually working fine. It uses the evdev driver as you may see from the log below:
```

[    23.573] (II) config/udev: Adding input device ImPS/2 ALPS GlidePoint (/dev/input/event7)
[    23.573] (**) ImPS/2 ALPS GlidePoint: Applying InputClass "evdev pointer catchall"
[    23.573] (II) Using input driver 'evdev' for 'ImPS/2 ALPS GlidePoint'

```

Now, I would like to do some advanced configuration, such as disabling tap-to-click or tapping-while-writing. But I've found no way to manage this through evdev -- all the documentation concerns the synaptics driver. This is installed but it seems I can't let it works: my touchpad is detected as an InputClass managed by "evdev".

Questions:
1) Is there a way to configure the touchpad without using the
"synaptics" driver?
2) Alternatively, how may I load the synaptics driver for my touchpad instead of evdev?



Cheers,
Ll.

---

### Post by MarjaE on 2011-05-27
I'm having the same problem in both 10.10 and 11.04. I installed Ubuntu on a used Sony Vaio E-series, and have been unable to disable tap-to-click.

I'm not very experienced with Ubuntu, and this has driven me up the wall - I backed up and reinstalled, and right now, I am using an older computer which lets me type without the aggravation of tap-to-click. So far I've tried installing synaptiks, I've tried the grub and xorg.conf.d hacks, I've tried using one of the mouse settings applications, which confirmed that the drivers were registering both taps and left-button clicks as button1 clicks. If the mouse driver merges the signals, I'm not sure how anything after that can separate the signals again and discard the taps.

P.S. I'm running standard Ubuntu, not Xubuntu.

---

### Post by MarjaE on 2011-10-17
There is a psmouse patch which worked fine in Ubuntu 11.04, but is not working in Xubuntu 11.10.

---

