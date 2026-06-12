---
title: "1366x768 second display (HP Laptop)"
date: 2012-04-06
forum: Hardware
---

### Post by thumbtak on 2012-04-06
I know this has been asked a lot, but every thread I find doesn't seem to provide the correct information.

I have an HP 530 Laptop.

I have a second monitor that is connected to the laptop. I am trying to set the display on the second monitor to 1366x768 (highest and clearest resolution). When I go to the display settings in "Applications => Settings => Settings Manager => Display" the highest setting I get is 1024x768.

When I run "xrandr -q" in the terminal I get...

[IMG]http://i39.tinypic.com/i5rzhc.png[/IMG]

Any suggestions on how to set the second display to 1366x768?

---

### Post by ahallubuntu on 2012-04-06
I wonder if your laptop has enough video memory to display at both of those resolutions (1280x800, 1366x768 ) at the same time?  It should, but you never know...

Many laptops allow you to toggle display modes: one mode is having your laptop screen OFF displaying only to the external monitor.  Can you switch into that mode?  If so, does it display correctly at 1366x768?  (Or can it?)  If so...then maybe it really can't display at the high resolution on both monitors at the same time.

Does your laptop have 2GB or only 1GB of RAM?  More RAM should allow more shared video RAM.  Some BIOSes also have options in BIOS Setup to set the amount of video RAM that is shared, but others allocated it automatically.

---

### Post by thumbtak on 2012-04-07
I used a program called "Multiple Screens" to turn off the laptops display and leave just the VGA display on. It only gave me 1024x768 or lower. If I remember correctly, I was able to set a much higher resolution on my 42" HDTV leaving both displays on as cloned. As for the RAM, how do I find out how much video RAM I have?

---

### Post by ahallubuntu on 2012-04-07
Could be that your laptop is having trouble detecting the exact monitor you have, if it can detect a higher resolution on your TV.

One way to tell how much video RAM is in use is to see how much ACTUAL RAM you have left in Ubuntu.  Try the "System Monitor" tool.

---

### Post by thumbtak on 2012-04-07
This is what "System Monitor" tells me.

[IMG]http://i42.tinypic.com/1zwgklx.png[/IMG]

I have a "Dell E1609Wc" monitor. 

Here is some pictures of the monitor that I found online.

[IMG]http://i39.tinypic.com/2ahten9.jpg[/IMG]
[IMG]http://i41.tinypic.com/2mri6x3.jpg[/IMG]

---

