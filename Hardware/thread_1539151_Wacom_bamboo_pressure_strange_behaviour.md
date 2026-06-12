---
title: "Wacom bamboo pressure strange behaviour"
date: 2010-07-26
forum: Hardware
---

### Post by Cezzare on 2010-07-26
Hello! Nice to meet everyone!

Fisrtly, thank you very much for  reading, I'm an Ubuntu Karmic user, and one of my hobbies is drawing, to  do this in the computer I use a wacom bamboo ctl-460 tablet.

Well,  I've found here posts about problems of users having no pressure  sensitivity on graphic editing software with wacom pen tablets. A while  ago I had this problem, and the solution was quite simple. For some time  things worked very well, but recently (a couple of hours ago actually) I  updated the kernel. Of course this rendered the tablet useless and I  had to reinstall the driver. After doing so and adding the needed  configuration it was seemingly working again. But... it was then that I  came across this "Problem":

I created a new document on GIMP and  started painting. I had the brush tip size controlled by the tablet's  pressure, so I started to draw lines expecting the ussual behaviour;  progressively increasing the applied pressure would proggresively  increase the line's thickness. Normally, after reaching the top pressure  level, the line's thickness should remain stable at a maximum value  until there was a pressure drecreasing or the pen was lifted from thet  tablet's surface; but instead of it I got this:

GIMP:

[IMG]http://img29.imageshack.us/img29/853/bug1k.jpg[/IMG]

Whever  I reached a "Top" pressure, the line's thickness dropped to a minimal  value. I tought it was maybe a problem with the GIMP, but I tested in  Mypaint and Krita, getting the same result in all cases, the green  outline symbolizes the stroke trayectory I was hoping to get: 

Mypaint:
[IMG]http://img834.imageshack.us/img834/5430/bug2x.jpg[/IMG]

Krita:

[IMG]http://img838.imageshack.us/img838/6969/bug3.jpg[/IMG]

I've  tried however to change the pressure curve's values, but the result  remains the same, I can't draw lines applying full pressure without them  to vanish at some point, I can try to simply draw with applying full  pressure on every stroke but it's very unconfortable to work that way. I  think it may be a driver problem but I'm not quite sure as I'm  relatively new with this kernel driver compiling stuff, I'm still  learning. The general information I can give you is:

Laptop: Compaq presario V3317la
System: Ubuntu 10.04 32 bit
Graphics driver: nvdida ver 195.36.24 (current)
kernel version: 2.6.32-24
x server version: 1.7.6
Driver used:  xf86-input-wacom-0.10.7
gnome version: 2.30.2

I  additionally can supply any other informatione needed to find a  workaround for this issue. However thank you so much in advance :D

---

### Post by Favux on 2010-07-26
Hi Cezzare,

Welcome to Ubuntu forums!

Nice post.  The pressure curve was fixed with a patch to xf86-input-wacom about 10 days ago.  So it should be fixed in the recently released 0.10.8 tar or by cloning the git.  See II. in the [Bamboo HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").  You might want to update the wacom.ko also (I.), depending on the version you're using.

Hope this helps.

---

### Post by Cezzare on 2010-07-27
Hello! Thank you so much, it worked indeed! Your guide is very very helpful, I'm happy to have the tablet running again :D, thanks!

---

