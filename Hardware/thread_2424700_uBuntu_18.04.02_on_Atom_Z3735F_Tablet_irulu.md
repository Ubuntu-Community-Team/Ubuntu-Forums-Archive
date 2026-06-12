---
title: "uBuntu 18.04.02 on Atom Z3735F Tablet irulu"
date: 2019-08-13
forum: Hardware
---

### Post by eurekalos on 2019-08-13
Hello, i don't know exactly where i need to post this.

So i gonna explain the best i could ;)

Tablet Irulu Walk'n'book 3 (model W21) based on Windows 8.1.

I've install ubuntu 18.04.02 and mad several test with kernels (5.0, 5.1 etc) and ubuntu 19.04 and other flavor (lubuntu, xubuntu, mint)

I use the script isorespin.sh of Linuxium to create a bootable ISO with bootia32.efi (BIOS 32 bits, OS 64bits).

I'm able to run ubuntu 18.04.02 on my tablet but i need to use "nomodeset" into grub command for the internal display.
So i've use it one time and enable SSH acces on my tablet.
Whe i try to put a HDMI screen it works but the screen of the tablet stay blank:
[[IMG]https://pix.tdct.org/upload/thumb/1558916543.jpg[/IMG]]("https://pix.tdct.org/upload/original/1558916543.jpg")

It's a Bay Trail CPU Z3735F and i'm unable to use the tablet without nomodeset because the screen turn blank.
But i can check the resolution of my screens:
[[IMG]https://pix.tdct.org/upload/thumb/1558916418.jpg[/IMG]]("https://pix.tdct.org/upload/original/1558916418.jpg")

If anyone had any idea ?

I work on this tablet for more than a year xD

Here is my screen informations (DSI-1 is my internal screen)
```
[COLOR=#FFFFFF]eureka@W21-Theory:~$ xrandr[/COLOR]Screen 0: minimum 320 x 200, current 1920 x 1280, maximum 8192 x 8192
DSI-1 connected 800x1280+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   800x1280      61.79*+
   1280x800      59.99    59.97    59.81    59.91  
   1280x720      60.00    59.99    59.86    59.74  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   1024x576      59.95    59.96    59.90    59.82  
   960x600       59.93    60.00  
   960x540       59.96    59.99    59.63    59.82  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   864x486       59.92    59.57  
   800x512       60.17  
   700x525       59.98  
   800x450       59.95    59.82  
   640x512       60.02  
   720x450       59.89  
   700x450       59.96    59.88  
   640x480       60.00    59.94  
   720x405       59.51    58.99  
   684x384       59.88    59.85  
   680x384       59.80    59.96  
   640x400       59.88    59.98  
   576x432       60.06  
   640x360       59.86    59.83    59.84    59.32  
   512x384       60.00  
   512x288       60.00    59.92  
   480x270       59.63    59.82  
   400x300       60.32    56.34  
   432x243       59.92    59.57  
   320x240       60.05  
   360x202       59.51    59.13  
   320x180       59.84    59.32  
DP-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 510mm x 287mm
   1920x1080     60.00*+  60.00    50.00    50.00    50.00    59.94  
   1920x1080i    60.00    60.00    50.00    50.00    59.94  
   1680x1050     59.88  
   1280x1024     60.02  
   1440x900      59.90  
   1280x800      59.91  
   1152x864      75.00  
   1280x720      60.00    50.00    59.94  
   1024x768      70.07    60.00  
   800x600       60.32    56.25  
   720x576       50.00    50.00  
   720x576i      50.00    50.00  
   720x480       60.00    60.00    59.94    59.94  
   720x480i      60.00    60.00    59.94    59.94  
   640x480       66.67    60.00    59.94    59.94  
   720x400       70.08  
DP-2 disconnected (normal left inverted right x axis y axis) [COLOR=#FFFFFF]HDMI-2 disconnected (normal left inverted right x axis y axis)[/COLOR]
```

---

