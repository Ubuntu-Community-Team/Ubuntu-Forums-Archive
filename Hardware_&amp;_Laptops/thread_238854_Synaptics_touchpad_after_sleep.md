---
title: "Synaptics touchpad after sleep"
date: 2006-08-18
forum: Hardware &amp; Laptops
---

### Post by jrb114 on 2006-08-18
Hi,

I'm trying to sort out the one remaining problem with a sony vaio VGN FS315S. It sleeps fine, usually hibernates fine, I can change the brightness etc...

Normally I run it with the touchpad tapping turned off. But, after waking from sleep, the touchpad (Synaptics), always reverts to tapping on. I've tried the usual:

Option MaxTapTime "0"

In xorg.conf, which works, until it comes back up from sleep. I've tried using qsynaptics, which lets me disable tapping from inside GNOME when the laptop wakes up, but even this doesn't always work.

Does anyone have any ideas? Is this a known bug?

Thanks,

James

---

### Post by jrb114 on 2006-08-18
Hey,

Just to let anyone know, I've found a way around this.

Taken from here
[https://launchpad.net/distros/ubuntu/+source/xorg-driver-synaptics/+bug/18605](https://launchpad.net/distros/ubuntu/+source/xorg-driver-synaptics/+bug/18605)

```

sudo gedit /etc/default/acpi-support

```

And add 
```

DOUBLE_CONSOLE_SWITCH=true

```

To the end of the file. Save it, and when the laptop wakes, the touchpad remembers that it isn't supposed to be tapping, and the scrolling works too.

---

