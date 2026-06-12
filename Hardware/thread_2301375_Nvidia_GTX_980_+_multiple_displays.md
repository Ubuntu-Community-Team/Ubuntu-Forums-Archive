---
title: "Nvidia GTX 980 + multiple displays"
date: 2015-11-02
forum: Hardware
---

### Post by Carl_Danley on 2015-11-02
I'm trying to get my desktop machine working with multiple displays. I really need them for work and can't skimp on having a single monitor. Anyways, here is the output for `xrandr -q`:

```
Screen 0: minimum 8 x 8, current 3520 x 1080, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected 800x600+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   800x600        60.3*+
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
DP-3 connected primary 1920x1080+800+0 (normal left inverted right x axis y axis) 531mm x 298mm
   1920x1080      60.0*+   59.9     50.0     60.1     60.0     50.0  
   1680x1050      60.0  
   1600x900       60.0  
   1280x1024      75.0     60.0  
   1280x800       59.8  
   1280x720       60.0     59.9     50.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   720x576        50.0     50.1  
   720x480        59.9     60.1  
   640x480        75.0     59.9     59.9  
DP-4 disconnected (normal left inverted right x axis y axis)
DP-5 connected 800x600+2720+32 (normal left inverted right x axis y axis) 0mm x 0mm
   800x600        60.3*+
Unknown-0 disconnected (normal left inverted right x axis y axis)
```

I need DVI-I-1 and DP-5 to both be at 1920x1080... I've tried a bunch of stuff but I'm not really great at figuring this out as it's been awhile since I've used Ubuntu desktop and a lot has changed since then. Please let me know how I can help provide the information needed to debug this together. 1 monitor (that works) is HDMI and the other 2 that are connected are both Display Ports; no matter what I do, they're unrecognized and won't go past 800x600 resolution...

Thanks in advance!!!

---

### Post by Carl_Danley on 2015-11-02
I could really use the help!!

---

### Post by blm-ubunet on 2015-11-03
This card needs signed firmware that is only available in nVidia proprietary driver (blob).
I believe it can be extracted & then used/loaded by nouveau but performance will be baseline.

Just install nVidia driver (as recommended by additional drivers) & then use nVidia-settings to configure displays.
You have to reboot after driver install to get the kernel component working.

There is a safe nVidia driver ppa avail. for ubuntu for when you need the latest driver release.

---

### Post by Carl_Danley on 2015-11-09
I was able to get everything working by install 15.10 and selecting the nvidia-binary from the additional drivers tab (as you suggested; thank you!). However, my next problem is that the main monitor works for 1920x1080 resolution and the 2 side monitors (left and right) only work at 1360x768 max; they are also marked as "Unknown Displays". Any idea how I can fix this?

---

### Post by blm-ubunet on 2015-11-11
Can you post (as attachment) your /var/log/Xorg.0.log file ?

---

### Post by Carl_Danley on 2015-11-11
Sure, here is my Xorg.0.log file: [https://gist.github.com/carldanley/75b9b51681a72e14aa98](https://gist.github.com/carldanley/75b9b51681a72e14aa98). Let me know what else I can help with; I really appreciate your help!!!!

---

### Post by blm-ubunet on 2015-11-12
The GTX980 max screen size is 5120x3200

3x 1920 > 5120.
2x 1920 + 1280 = 5120.

So can't have (3) 1920 monitor side by side in landscape mode (at least in twinview one virtual  desktop).

But your log shows auto selected mode of 3968 x 1080.. not sure why.. One of your display connections is limited to 165MHz (crappy single link HDMI)?

Use nvidia-settings & try change resolutions & drag one monitor into different position so all (3) are not side-by-side.

There too little useful info in the xorg log file.. would need to add modeline debugging command to /etc/X11/xorg.conf

---

