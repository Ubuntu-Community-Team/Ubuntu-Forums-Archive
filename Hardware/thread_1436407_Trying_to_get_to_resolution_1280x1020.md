---
title: "Trying to get to resolution 1280x1020"
date: 2010-03-22
forum: Hardware
---

### Post by McCorkis on 2010-03-22
Sorry Newbie here im trying to get my ubuntu on my laptop its a hp compaw nc6400 with a intel 945 card and im looking to get 1280*1020 when im stuck at the default 1280*800.

---

### Post by lykwydchykyn on 2010-03-22
If the technical specs are anything to go by, your hardware won't do any better than 1280x800, or maybe 1440x900 if you have the WXGA+ monitor.

[http://h18000.www1.hp.com/products/quickspecs/12446_ca/12446_ca.HTML](http://h18000.www1.hp.com/products/quickspecs/12446_ca/12446_ca.HTML)

---

### Post by McCorkis on 2010-03-22
with windows 7 it supports it

---

### Post by lykwydchykyn on 2010-03-22
> **McCorkis said:**
> with windows 7 it supports it

I'm just going by the specs on the website.

Can you open a terminal, type "xrandr" and paste the output here?

---

### Post by McCorkis on 2010-03-22
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 4096 x 4096
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 304mm x 190mm
   1280x800       59.9*+
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
DVI1 disconnected (normal left inverted right x axis y axis)
TV1 disconnected (normal left inverted right x axis y axis)

---

### Post by Tom.Gee on 2010-03-22
1280 x 1020 sounds bizarre.  I've used CRTs at 1280 x 1024, but I've never seen a laptop with a native 5:4.  5:4 is closer to square than the old standard of 4:3.  If your laptop is a widescreen, then the only support for 1280 x 1024 would be with the screen scrolling as you move the mouse left to right, thus showing you a 1280 x 1024 desktop through a 1280 x 800 window.  Double check your windows 7 video resolution.  It may not be set at 1280 x 1020.

---

### Post by McCorkis on 2010-03-22
sry yes im looking for 1280x1024 sry

---

### Post by Yellow Pasque on 2010-03-22
Your screen is only 1280x800. [http://www.notebookreview.com/default.asp?newsID=3110](http://www.notebookreview.com/default.asp?newsID=3110)
How do you get a larger resolution under Windows?

---

### Post by rpared01 on 2010-03-22
at work i have a spare nc6400 with an ati video card in it and it can only do 1280x800

---

### Post by lykwydchykyn on 2010-03-22
> **McCorkis said:**
> Screen 0: minimum 320 x 200, current 1280 x 800, maximum 4096 x 4096
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 304mm x 190mm
   1280x800       59.9*+
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
DVI1 disconnected (normal left inverted right x axis y axis)
TV1 disconnected (normal left inverted right x axis y axis)

I would say based on this output you aren't going to get better than 1280x800.

Since it's an Intel card, the best available driver is already built into the kernel, there is not a proprietary driver you can download to enhance functionality as with Nvidia or Ati cards.

Your screen is a widescreen (8:5 aspect) according to that output and the published specs, so it would be odd for it to support a standard 5:4 or 4:3 resolution, and it'd look pretty squashed if you managed to get it to.

If you really must absolutely just have this resolution, about the only thing I can suggest is that you could manually create an xorg.conf file and put in your own list of available modes.  It probably won't work, though, and involves a certain amount of command line/config-file work which you may not want to bother with.

Still, if you want to go that route, here's a good place to start reading:

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by Tom.Gee on 2010-03-23
> **Temüjin said:**
> Your screen is only 1280x800. [http://www.notebookreview.com/default.asp?newsID=3110](http://www.notebookreview.com/default.asp?newsID=3110)
How do you get a larger resolution under Windows?Most laptops under Windows will let you set the screen size to anything the video card will generate, and will then scroll the screen so you can reach the parts that are rendered beyond the physical display.  I'm an idiot - I mentioned scrolling left-right.  Since 1280 is his native width, he's scrolling up-down to see the 224 bitlines rendered offscreen.  This is usually a function of the video driver, so the functionality should be available to linux users as well if using the manufacturer's linux driver.

---

### Post by cascade9 on 2010-03-23
1280 x 800 is the max native resolution- 

[http://reviews.cnet.com/laptops/hp-compaq-nc6400-core/4507-3121_7-31851193.html](http://reviews.cnet.com/laptops/hp-compaq-nc6400-core/4507-3121_7-31851193.html)

[http://www.notebookreview.com/assets/11891.pdf](http://www.notebookreview.com/assets/11891.pdf)

---

