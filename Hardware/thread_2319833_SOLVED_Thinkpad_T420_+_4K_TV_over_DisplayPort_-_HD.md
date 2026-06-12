---
title: "SOLVED: Thinkpad T420 + 4K TV over DisplayPort - HDMI adapter - possible?"
date: 2016-04-07
forum: Hardware
---

### Post by VitasLoWang on 2016-04-07
Hello, I have Lenovo T420 and Ubuntu 14.04. It works OK in my office where I have two monitors connected to it: VGA and DP with laptop display off (with it on there are crazy artifacts) and it is OK. In BIOS I have set display to "discrete graphics" which is Nvidia NVS4200 GPU. Optimus does work only if I boot into Windows.
I wanted to connect a Samsung 4K TV to it, but it has only HDMI input and laptop has DisplayPort++ 1.2 output, so I bought this expensive DisplayPort - HDMI converter cable but it seems useless so far :(
When I boot without the DP cable connected and connect the TV after I am logged into mate desktop, it shows "Samsung electric 47" in "monitors" applet correctly and even sets the right 4K resolution at 30Hz, but the TV has no signal. I have nouveau driver installed. Maybe it is incompatible with something. Changing resolution to lower or disconnecting the TV usually results in a [total screen scramble and necessity to turn off laptop by holding power button]("https://goo.gl/photos/LRi2r5hkBgoXrrvu6").
```
[SIZE=2][COLOR=#383838][FONT=gotham]vitas@T420-vitas:~$ xrandr[/FONT][/COLOR]
[COLOR=#383838][FONT=gotham]Screen 0: minimum 320 x 200, current 1600 x 900, maximum 8192 x 8192[/FONT][/COLOR]
[COLOR=#383838][FONT=gotham]LVDS-1 connected 1600x900+0+0 (normal left inverted right x axis y axis) 310mm x 174mm[/FONT][/COLOR]
[COLOR=#383838][FONT=gotham]1600x900 60.0*+[/FONT][/COLOR]
[COLOR=#383838][FONT=gotham]1152x864 60.0 [/FONT][/COLOR]
[COLOR=#383838][FONT=gotham]1024x768 59.9 [/FONT][/COLOR]
[COLOR=#383838][FONT=gotham]800x600 59.9 [/FONT][/COLOR]
[COLOR=#383838][FONT=gotham]640x480 59.4 [/FONT][/COLOR]
[COLOR=#383838][FONT=gotham]720x400 59.6 [/FONT][/COLOR]
[COLOR=#383838][FONT=gotham]640x400 60.0 [/FONT][/COLOR]
[COLOR=#383838][FONT=gotham]640x350 59.8 [/FONT][/COLOR]
[COLOR=#383838][FONT=gotham]VGA-1 disconnected (normal left inverted right x axis y axis)[/FONT][/COLOR]
[COLOR=#383838][FONT=gotham]DP-1 disconnected (normal left inverted right x axis y axis)[/FONT][/COLOR]
[COLOR=#383838][FONT=gotham]DP-2 disconnected (normal left inverted right x axis y axis)[/FONT][/COLOR]
[COLOR=#383838][FONT=gotham]DP-3 disconnected (normal left inverted right x axis y axis)

[/FONT][/COLOR][/SIZE][COLOR=#383838][FONT=gotham]vitas@T420-vitas:~$ lsmod | grep nouveau
[/FONT][/COLOR]
[COLOR=#383838][FONT=gotham]nouveau 1097199 3 
mxm_wmi 13021 1 nouveau
i2c_algo_bit 13413 1 nouveau
ttm 93424 1 nouveau
drm_kms_helper 55071 1 nouveau
drm 303102 5 ttm,drm_kms_helper,nouveau
wmi 19177 2 mxm_wmi,nouveau
video 19476 1 nouveau

[/FONT][/COLOR]
[COLOR=#383838][FONT=gotham]vitas@T420-vitas:~$ dpkg -l|grep nouveau
ii libdrm-nouveau2:amd64 2.4.60-2~ubuntu14.04.1 amd64 Userspace interface to nouveau-specific kernel DRM services -- runtime
[/FONT][/COLOR]
[COLOR=#383838][FONT=gotham]ii xserver-xorg-video-nouveau 1:1.0.10-1ubuntu2 amd64 X.Org X server -- Nouveau display driver[/FONT][/COLOR]
```

I have tried Gnome flashback and the whole system freezes right after connecting the TV there :-\ And I also wonder why xrandr shows DP-1,2 and 3 :o Is it because it is DisplayPort++ allowing me to connect more monitors?
I wonder if the converter may be faulty or the GPU in my thinkpad, because I have Windows 7 on another hdd in ultrabay and in it it also does not really work properly (but does not freeze the system at least :) FullHD signal works and TV shows it OK. Any bigger resolution causes split second image flickers on the TV alternating with black image. But with Linux it does not even try nothing and TV still shows "no signal" !
Any ideas or suggestions what can I do?

---

### Post by Alex_Metivier on 2016-04-08
if you actually have a VGA port on your laptop connect directly to the port. you would also need to change the settings on the laptop to allow projector only display and that could be the problem. if you did not change the setting to keep the laptop display off and only have the screen the TV then it will probably not work.

---

### Post by VitasLoWang on 2016-04-08
What do you mean to connect directly to VGA port? VGA port for sure will not work with 4K ;) 
I tried again in Windows the win+p projector only mode an boom I have 4K on the TV! So I tried the same in Ubuntu - connecting the TV and then switching off the laptop display and boom not... laptop screen off and TV still no signal :( And as I wrote before - disconnecting the cable caused screen scramble and necessity to force power off laptop again. I guess I will try Nvidia driver instead of nouveau...

---

### Post by VitasLoWang on 2016-04-10
so...nobody knows? Please just tell me you who connect your Ubuntu laptop to tv or monitor and have it in external mode only - do you do it like this? Connect the external display and then switch off laptop display in monitor options?

---

### Post by VitasLoWang on 2016-04-10
So in case anyone is interested - I solved it. sudo apt-get nvidia-current, reboot and I have two monitors - laptop with 1600x900 and TV with 3840x2160 @30Hz no problem. Seem like nouveau needs some fixing. The only minor issue that happened is that everything like text and window titles now seem to be bigger, but I hope there is some settings for that.

---

