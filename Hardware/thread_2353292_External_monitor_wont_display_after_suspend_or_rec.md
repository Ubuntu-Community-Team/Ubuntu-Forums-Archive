---
title: "External monitor wont display after suspend or reconnect."
date: 2017-02-20
forum: Hardware
---

### Post by jcopeland on 2017-02-20
I am running Ubuntu 16.10 on a Razer Blade Stealth late 2016. It only has Intel video.

I connect an external monitor at work. My issue is that for it to work I have to connect it and then reboot the computer. If I disconnect and reconnect the external monitor in not detected. Also, if the computer suspends even while connected, when it wakes it will not detect the monitor.

```
[INDENT][FONT=courier new]$ xrandr[/FONT][/INDENT]
[INDENT][FONT=courier new]Screen 0: minimum 320 x 200, current 5160 x 3600, maximum 8192 x 8192[/FONT][/INDENT]
[INDENT][FONT=courier new]eDP-1 connected primary 2560x1440+1260+2160 (normal left inverted right x axis y axis) 277mm x 155mm[/FONT][/INDENT]
[INDENT][FONT=courier new]   2560x1440     59.95*+  39.97  [/FONT][/INDENT]
[INDENT][FONT=courier new]   1920x1440     60.00  [/FONT][/INDENT]
[INDENT][FONT=courier new]  ...deleted unused resolutions to shorten[/FONT][/INDENT]
[INDENT][FONT=courier new]DP-1 connected 5160x2160+0+0 (normal left inverted right x axis y axis) 800mm x 335mm[/FONT][/INDENT]
[INDENT][FONT=courier new]   3440x1440     49.99*+  29.99  [/FONT][/INDENT]
[INDENT][FONT=courier new]   2560x1080     60.00  [/FONT][/INDENT]
[INDENT][FONT=courier new] ...deleted unused resolutions to shorten[/FONT][/INDENT]
[INDENT][FONT=courier new]HDMI-1 disconnected (normal left inverted right x axis y axis)[/FONT][/INDENT]
[INDENT][FONT=courier new]DP-2 disconnected (normal left inverted right x axis y axis)[/FONT][/INDENT]
[INDENT][FONT=courier new]HDMI-2 disconnected (normal left inverted right x axis y axis)[/FONT][/INDENT]

```
One starting point I would like to look at but am not familiar with is seeing hardware connection events. How can that be accomplished.

---

