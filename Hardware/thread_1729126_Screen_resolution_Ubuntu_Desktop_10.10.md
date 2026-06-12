---
title: "Screen resolution Ubuntu Desktop 10.10"
date: 2011-04-14
forum: Hardware
---

### Post by sprouty on 2011-04-14
Hi,

I'm having problems change my screen resolution from 800X600 to 1024X768

I've tried using ARandR, xrandr -s 1024x768 and the file /etc/X11/xorg.conf doesn't exists. I would be grateful if someone could help me on this.

[http://www.ebuyer.com/product/261377](http://www.ebuyer.com/product/261377)

cheers,

Sprouty.

---

### Post by BicyclerBoy on 2011-04-14
The xorg.conf is not needed anymore but it can still be very useful.

What video h/w ?
What video h/w driver?
Output of xrandr -q
Post the file as attachment 
/var/log/Xorg.0.log

The above file will prob answer all the above questions..

---

### Post by sprouty on 2011-04-22
Hi,

I had to upload Xorg log inside a zip file

Xrandr output:

```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0*
   640x480        60.0

```

I'm not sure which graphics card the laptop uses, would you be able to help me find out?

Cheers,

Sprouty

---

