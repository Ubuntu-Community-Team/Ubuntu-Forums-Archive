---
title: "increase monitor resolution with maxtor DualHead2Go"
date: 2011-08-01
forum: Hardware
---

### Post by aa-hcl on 2011-08-01
Hi,

I have ubuntu 11.04 (2.6.38-10-generic) on dell laptop E6520, graphic card nvidia NVS 4200M with latest nvidia driver version (270.41.06), laptop display is 1920x1080.

I attached as external display the maxtor dual head2go box with two 1920x1200 monitors. Nvidia recognises it as "maxtor" and allows me to set the maximum resolution of 2560x1024, so I have in total laptop screen 1920x1080 and a big screen of two monitors - 2560x1024.

Obviously, I want to have the maxtor box having the resolution of 3840x1200 (it is possible by the hardware - on Win7 it works, but only after installing maxtor configuration program).

How can I do that?

I tried so far 



[CODE] 
aa@aa-i7:~$ cvt 5760 1080 60
# 5760x1080 59.99 Hz (CVT) hsync: 67.19 kHz; pclk: 519.25 MHz
Modeline "5760x1080_60.00"  519.25  5760 6128 6744 7728  1080 1083 1093 1120 -hsync +vsync
aa@aa-i7:~$ xrandr --newmode "5760x1080_60.00"  519.25  5760 6128 6744 7728  1080 1083 1093 1120 -hsync +vsync
xrandr: Failed to get size of gamma for output default
aa@aa-i7:~$ xrandr --addmode default "5760x1080_60.00"
xrandr: Failed to get size of gamma for output default
aa@aa-i7:~$ xrandr --output default --mode "5760x1080_60.00"
xrandr: Failed to get size of gamma for output default
xrandr: Configure crtc 0 failed
 [\CODE]

and the same for 3840x1200; 5760x1200: the output of xrandr is:

[CODE]
aa@aa-i7:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 175, current 4480 x 1080, maximum 5760 x 1200
default connected 4480x1080+0+0 0mm x 0mm
   1920x1080      50.0     51.0     52.0    141.0  
   1680x1050      53.0  
   1600x1024      54.0  
   1440x900       55.0  
   1400x1050      56.0  
   1360x768       57.0     58.0  
   1280x1024      59.0     60.0  
   1280x960       61.0  
   1152x864       62.0     63.0     64.0     65.0     66.0     67.0  
   1024x768       68.0     69.0     70.0     71.0     72.0     73.0  
   960x720        74.0  
   960x600        75.0  
   960x540        76.0  
   928x696        77.0  
   896x672        78.0     79.0  
   840x525        80.0     81.0     82.0     83.0     84.0  
   832x624        85.0  
   800x600        86.0     87.0     88.0     89.0     90.0     91.0     92.0     93.0     94.0     95.0  
   800x512        96.0  
   720x450        97.0  
   720x400        98.0  
   700x525        99.0    100.0    101.0    102.0  
   680x384       103.0    104.0  
   640x512       105.0    106.0    107.0  
   640x480       108.0    109.0    110.0    111.0    112.0    113.0  
   640x400       114.0  
   640x350       115.0  
   576x432       116.0    117.0    118.0    119.0    120.0    121.0    122.0  
   512x384       123.0    124.0    125.0    126.0    127.0  
   416x312       128.0  
   400x300       129.0    130.0    131.0    132.0    133.0  
   360x200       134.0  
   320x240       135.0    136.0    137.0    138.0  
   320x200       139.0  
   320x175       140.0  
   4480x1080     141.0* 
   5760x1200_60.00   59.9  
   5760x1080_60.00   60.0  
  3840x1200_60.00 (0x1f3)  386.8MHz
        h: width  3840 start 4104 end 4512 total 5184 skew    0 clock   74.6KHz
        v: height 1200 start 1203 end 1213 total 1245           clock   59.9Hz
 [\CODE]

Can anyone help me to set up the correct resolution of maxtor box?

---

