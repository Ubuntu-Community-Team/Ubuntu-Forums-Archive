---
title: "extended monitor flickering issue using xrandr+vnc"
date: 2019-10-03
forum: Hardware
---

### Post by staxer on 2019-10-03
I tried to use my android tablet as a second monitor for my laptop  with vnc+xrandr by following this tutorial [https://sangams.com.np/using-android-pc-as-a-second-monitor-in-linux/](https://sangams.com.np/using-android-pc-as-a-second-monitor-in-linux/) .Whenever my tablet connect to my laptop

the screen of my tablet  flicker with all vnc program for android. between this it's my laptop setup
os : ubuntu 18.04 LTS
kernel : 5.2.14
APU : ryzen 5 2500u,vega 8
laptop : HP-Pavilion-Laptop-15-cw0xxx

```

$ xrandr

[INDENT]Screen 0: minimum 320 x 200, current 2646 x 800, maximum 16384 x 16384

eDP connected primary 1366x768+1280+0 (normal left inverted right x axis y axis) 344mm x 194mm

1366x768      60.06*+  40.01

1280x720      60.06

1024x768      60.06

800x600       60.06
640x480       60.06

HDMI-A-0 disconnected 1280x800+0+0 (normal left inverted right x axis y axis) 0mm x 0mm

1280x800_virt  59.81*

[/INDENT]
```

---

