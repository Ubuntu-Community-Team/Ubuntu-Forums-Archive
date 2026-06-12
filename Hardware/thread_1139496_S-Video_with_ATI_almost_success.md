---
title: "S-Video with ATI almost success"
date: 2009-04-27
forum: Hardware
---

### Post by JKoder on 2009-04-27
Hello everyone.
I must say that i have an ATI Xpress 1100 video card and sadly is now suported as a legacy card . No problem.
I am preety satisfyed with the "radeon" driver.
Now, one of this days i have tryed to make my sVideo work using the radeon man page and the radeonTV Wiki. [http://www.x.org/wiki/radeonTV](http://www.x.org/wiki/radeonTV)
Ok after a few test i have managet ot get something on my TV but the image was junky ( full of horizontal lines ) and the image was jumping on my TV. Basicaly i could not distinguis anything on my TV.
So mabye one of yo can help me here to fix this issue.Mabye someone had this problem before . 
So if you like, can you please help me ?
Thank you.

---

### Post by aaboelela on 2009-05-13
Hi,

check this:

[http://mfbernardes.com/drupal/content/finally-i-got-tv-out-s-video-working-my-thinkpad-t42](http://mfbernardes.com/drupal/content/finally-i-got-tv-out-s-video-working-my-thinkpad-t42)

To enable S-Video Out:
> xrandr --output S-video --set load_detection 1 
xrandr --output S-video --auto 
xrandr --output LVDS --offNow to go back to normal:
> xrandr --output LVDS --auto 
xrandr --output S-video --off 

---

### Post by aaboelela on 2009-05-13
Also you can create that in script files (e.g. **tvon** and **tvoff**) to make it easy, as following:

1. create **tvon** script file:
> cd /usr/bin
sudo vim tvonThen insert (type **i** to goto insert mode):
> xrandr --output S-video --set load_detection 1 
 xrandr --output S-video --auto 
 xrandr --output LVDS --offThen type **Esc** to go back to command mode, then save and exit using : x or :w then :q

2. Create **tvoff** script file:
> cd /usr/bin
sudo vim tvoffThen insert (type **i** to goto insert mode):
> xrandr --output LVDS --auto 
 xrandr --output S-video --off Then type **Esc** to go back to command mode, then save and exit using : x or :w then :q

3. Make the script files exectable:

> sudo chmod 777 tv*Now connect the S-Video to your TV, then type **tvon** to enable tv/s-video output, then later type in the command line **tvoff** to go back to normal.

---

