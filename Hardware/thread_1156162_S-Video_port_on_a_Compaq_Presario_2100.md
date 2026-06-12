---
title: "S-Video port on a Compaq Presario 2100"
date: 2009-05-11
forum: Hardware
---

### Post by emacbri on 2009-05-11
Hi,

I am running a Compaq Presario 2100 with a ATI Radeon IGP 3xx. It has a S-Video port and I recently found a use for it. But for some reason it dosen't work in Ubuntu. It used to work fine in XP. Please someone help, I would like to use this port. Thanks.

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
xrandr --output S-video --off Also you can create that in script files (e.g. **tvon** and **tvoff**) to make it easy, as following:

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

