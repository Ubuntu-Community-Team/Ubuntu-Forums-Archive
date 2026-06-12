---
title: "Screen displays not correct resolution after update nvidia-340.101"
date: 2017-01-16
forum: Hardware
---

### Post by lilngu on 2017-01-16
Hi everyone,
I have Ubuntu-MATE 16.04 on my Dell M6400 with 17" lcd, resolution 1920x1200, my GPU is Nvidia Quadro Fx3700m.
Before all, I use ubuntu open-source driver (nouveau), but wanna the best performance with Fusion8 compositing, I try to install nvidia driver. I've installed nvidia-340 (340.101) from PPA, not directly from Nvidia website. After installation, I checked it in Additional Drivers and I see the list say "nvidia-340.101 from nvidia-340 (open-source)". I have no idea, I think it must be "proprietary driver"!
But that's not my big problem. The problem is resolution, my screen have resolution 1920x1200 for the best, but now the 1920x1200 option display not correct, it's still 1920x1200 but it's wrong.
This my old desktop screenshot. Look good, right?
[http://i.imgur.com/rGRzDTV.jpg](http://i.imgur.com/rGRzDTV.jpg)

And, this is after install driver. Everything seen bigger.
[http://i.imgur.com/rGIWFpH.jpg](http://i.imgur.com/rGIWFpH.jpg)

The resolution made me uncomfortable, it just like 1024x768, or worse.
But, this is not make sense.
I open Chrome browser, Chrome windows show anything big, just not right resolution and dpi.
[http://i.imgur.com/nEvG7Ot.png](http://i.imgur.com/nEvG7Ot.png)

But in Fusion8, anything show good, correct view.
[http://i.imgur.com/7MJ1nzF.png](http://i.imgur.com/7MJ1nzF.png)
I've tried to change resolution for bigger screen in xorg.conf; I change it to 2304x1440. Then, here what I get
[http://i.imgur.com/3KjTWrv.jpg](http://i.imgur.com/3KjTWrv.jpg)
The desktop show good, icon and anything smaller. In Chrome window, it show good but still blur on text and edge, not sharp as right resolution.
But In Fusion8 workview, it's terrible, anything seen bigger.
[http://i.imgur.com/CDPJAKW.png](http://i.imgur.com/CDPJAKW.png)
Yah! I really to be mad. Something wrong? I need help to fix this. I think it's about driver or xorg.conf.

---

### Post by ajgreeny on 2017-01-16
Please do not add large images inline in your posts. Either use links as I have done or add images as attachments with the paperclip in the toolbar.

If replying to a post you need to use the Reply to Post button, or Go Advanced if using the Quick reply box to see the paperclip icon.

---

### Post by Autodave on 2017-01-16
Did you pick the Nvidia driver to install or did you let Ubuntu chose it? There are newer drivers that might work better. I believe that 367.??? is the newest one.   The driver you are using is quite old: about 3 or 4 driver updates ago.

---

