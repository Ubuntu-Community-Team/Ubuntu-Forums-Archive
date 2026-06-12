---
title: "FAO Nvidia users with PAL TVs"
date: 2010-11-11
forum: Hardware
---

### Post by thecapsaicinkid on 2010-11-11
Just a heads up regarding something I've spent more than an hour or two trying to troubleshoot.

By default, the nvidia driver installed by Ubuntu (or rather nvidia-settings) seems to enable gpu scaling. This option will scale your requested mode to the mode your screen reports as its native (nvidia-auto-select) including its refresh. Most (all?) PAL screens will report a native mode using 50Hz. 

This causes problems when you switch to what you think is a 60Hz mode actually results in your screen recieving a 50Hz mode. 60fps videos will play too slowly or stutter badly Xorg will usually hit 100% cpu usage and other rather undesirable side effects.

This had me tearing my hair out for ages, my screen doesn't show on the OSD what refresh it is actually recieving so I was none the wiser.

You can test this out by switching to a 60Hz mode in nvidia-settings and then running the following command in a terminal

```

nvidia-settings -q RefreshRate | grep -o "[0-9][0-9].*Hz"

```If it reports 50.0Hz then you have the same problem, disable gpu scaling (set it to 'native') in nvidia-settings or system wide in your /etc/X11/xorg.conf.

I think Ubuntu package maintainers should set gpu scaling to false when the nvidia driver/nvidia-settings is installed for this very reason. A clean install of Ubuntu with an Nvidia card and a PAL screen will be locked to 50Hz and unable to playback 60fps video smoothly.

---

