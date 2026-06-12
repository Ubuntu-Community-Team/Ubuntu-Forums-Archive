---
title: "Reduce size of the screen... Im not talking about resolution"
date: 2024-12-04
forum: Hardware
---

### Post by 9acca9 on 2024-12-04
Hi i have an old projector and a Ubuntu in a pc attached.   
     The thing is my projection is too big for my "display" the sheet where i project (i dont know the word in english)   
     So, i want to reduce the size of the screen in Ubuntu.   
     How i can do that?   
     (i was using this projector in the pass with a raspberry py, and  with the raspberry pi i just put this in the config.txt file in /boot  and all work fine:   

```
# Display
disable_overscan=0

# uncomment the following to adjust overscan. Use positive numbers if console
# goes off screen, and negative if there is too much border
overscan_left=50
overscan_right=50
overscan_top=60
overscan_bottom=60
```     )   
     I try with xrandr like this (the values where just too see if the change is the kind of change im expecting):   
```
     xrandr --output HDMI-1 --transform 1.085,0,-50,0,1.18,-65,0,0,1   


```     But, dont work at all. With that the x and y from the top and left  change but the bottom and right dont change at all (i just lost part of  the screen)   
     Thanks

---

### Post by TheFu on 2024-12-04
In general, the fix for this is to move the projector to be closer to the wall or use projector controls to do the scaling.  I've owned 4 projectors over the decades and always look up the throw distance to ensure it fits my requirements on projection size.  Sometimes the projector I want doesn't work for my space, so I don't get it.

BTW, I use a r-pi v4 to drive my Epson.  Great for movies!  120inch projection makes any TV look tiny.  Think the projector is about 10 ft away from the wall, but I haven't measured in years.    Here's a throw-distance calculator: [https://www.projectorcentral.com/Epson-Home_Cinema_1080-projection-calculator-pro.htm](https://www.projectorcentral.com/Epson-Home_Cinema_1080-projection-calculator-pro.htm)  It is handy to have this calculator for your projector BEFORE purchase.

---

### Post by 9acca9 on 2024-12-04
Hi. Thank you very much. 
Yes i know that moving the projector can fix this. But the projector is in the perfect place to not bother in my space... except that... it is too big. BUT the solution of just changing the values in config.txt of the rpi was perfect. 
There is not something like that in ubuntu for a pc? 
in the other hand, yes, even the rpi4 was working excellent to play movies and music, etc.

---

### Post by TheFu on 2024-12-04
There might be kernel options that you can add to grub. IDK.
[https://www.dedoimedo.com/computers/linux-mint-cinnamon-hd-scaling.html](https://www.dedoimedo.com/computers/linux-mint-cinnamon-hd-scaling.html) might help.
I understand that KDE+Plasma handles this easily. I haven't used it.

BTW, you are using X/Windows tools, but recent versions of Ubuntu all use Wayland, not X/Windows.  Do those tools even work on a normal Ubuntu desktop?  Things that have been possible for a long time aren't under Wayland.

---

### Post by 9acca9 on 2024-12-04
Hi. 
Do you know what i have to look in kde+plasma? i use kde like 10 years ago i believe.
About x/windows tools it is because i cahnge for Xorg when login.

---

