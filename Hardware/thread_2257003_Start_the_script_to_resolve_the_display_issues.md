---
title: "Start the script to resolve the display issues"
date: 2014-12-16
forum: Hardware
---

### Post by gopukrishnan on 2014-12-16
I have installed ubuntu 14.04 in a new machine and found that the OS is not detecting the display resolutions correctly. I have followed the below link and it resolved the issue temporarily :
[http://askubuntu.com/questions/13783/external-monitor-resolution-doesnt-go-above-1024x768](http://askubuntu.com/questions/13783/external-monitor-resolution-doesnt-go-above-1024x768)
I have run the below commands :
```
xrandr --newmode "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
xrandr --addmode VGA1 "1368x768_60.00"
```

But when I logout and login, I have to run this command again. Is it possible for me have this settings permanently without running each time I login ?

Thanks

---

### Post by gopukrishnan on 2014-12-19
Not even a suggestion ! :(

---

### Post by pfeiffep on 2014-12-20
> **gopukrishnan said:**
> I have installed ubuntu 14.04 in a new machine and found that the OS is not detecting the display resolutions correctly. I have followed the below link and it resolved the issue temporarily :
[http://askubuntu.com/questions/13783/external-monitor-resolution-doesnt-go-above-1024x768](http://askubuntu.com/questions/13783/external-monitor-resolution-doesnt-go-above-1024x768)
I have run the below commands :
```
xrandr --newmode "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
xrandr --addmode VGA1 "1368x768_60.00"
```

But when I logout and login, I have to run this command again. Is it possible for me have this settings permanently without running each time I login ?

ThanksI'm intrigued by your particular problem so I did some searching myself because I have absolutely no experience with xrandr, nor with proprietary video drivers.That caveat out of the way I did find a couple links that just might help you make the changes permanent. Hopefully these links will provide direction for solving the screen resolution problem:[INDENT][http://askubuntu.com/questions/435997/how-can-one-change-login-screen-resolution-with-propreitary-graphic-driver-insta](http://askubuntu.com/questions/435997/how-can-one-change-login-screen-resolution-with-propreitary-graphic-driver-insta)

[http://askubuntu.com/questions/468298/resolution-changes-after-startup-login](http://askubuntu.com/questions/468298/resolution-changes-after-startup-login)

[http://askubuntu.com/questions/445957/why-dont-my-lightdm-conf-edits-affect-my-desktop-screen-resolution/446050#446050](http://askubuntu.com/questions/445957/why-dont-my-lightdm-conf-edits-affect-my-desktop-screen-resolution/446050#446050) 
[/INDENT]

---

