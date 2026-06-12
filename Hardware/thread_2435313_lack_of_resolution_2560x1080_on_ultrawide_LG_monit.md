---
title: "lack of resolution 2560x1080 on ultrawide LG monitor 21:9"
date: 2020-01-19
forum: Hardware
---

### Post by eriasari on 2020-01-19
I have a pc with dual boot Ubuntu 18.04.3 (gnome 3.28.4) and Windows 10 and an ATI/AMD Radeon HD 6700 Series card. My monitor LG 29WK500-P has a native resolution of 2560x1080. Windows detect it normally and everything works fine but Ubuntu is not found 2560x1080 in the list of resolutions and max resolution which I can set in ubuntu is 1920x1080. 

I tried add manually resolution ([https://www.leowkahman.com/2019/02/06/ultrawide-monitor-on-linux/](https://www.leowkahman.com/2019/02/06/ultrawide-monitor-on-linux/)) by *cvt* and *xrandr* commands. 
```

    $ xrandr 
    Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 16384 x 16384
    DisplayPort-0 disconnected (normal left inverted right x axis y axis)
    HDMI-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 798mm x 334mm
       1920x1080     50.00    59.99*   59.94  
       1680x1050     59.88  
       1600x900      60.00  
       1280x1024     75.02    60.02  
       1280x800      59.91  
       1152x864      75.00    59.97  
       1280x720      60.00    50.00    59.94  
       1024x768      75.03    60.00  
       832x624       74.55  
       800x600       75.00    60.32  
       720x576       50.00  
       720x480       60.00    59.94  
       640x480       75.00    60.00    59.94  
```

I tied with frequencies from 56 till 75 but mostly after set *xrandr output* screen was black, how ever when tried cvt with values 72,73,74,75 it showed screen similar like on screen below.

I tried also remove my Radeon from PC and connect monitor to integrated graphics  card and when Ubuntu started then it had resolution 2560x1080 (but then  nothing is showed during boot process, just when showed ubuntu login  screen). 
I used command:
```

    xvidtune -show
```

Which showed  used modeline and next I again put radeon card in PC and tried use this  modeline data which I got. Unfortunately after apply, it doesn't works and shows black  screen on monitor :(
I installed also the newest version of Ubuntu 19.10 (I had free space on my disk) but there also no detect resolution 2560x1080.
I have no any more idea what I can do. 
  


[IMG]https://i.stack.imgur.com/6sDOt.jpg[/IMG]

---

