---
title: "X1650 Problems/Issues"
date: 2007-09-19
forum: Hardware &amp; Laptops
---

### Post by bigpetey44 on 2007-09-19
Ok to put this short and simple, the ati drivers install, ive actually gotten to the point where i got both my screens setup and working (was quite nice), but i could NOT see my pointer, and when i could sometimes it was a translucent box or a wierd looking graphic.

Also, i get my resolution setup at 1440 x 900 (19 inch widescreens) at 24 bit. Also when i check fglrxinfo and glx info, i get the card showing up, but everything still using MESA and no direct rendering.

[http://i130.photobucket.com/albums/p247/bigpetey44/Screenshot-1-1.png](http://i130.photobucket.com/albums/p247/bigpetey44/Screenshot-1-1.png)
[http://i130.photobucket.com/albums/p247/bigpetey44/Screenshot-2.png](http://i130.photobucket.com/albums/p247/bigpetey44/Screenshot-2.png)

There you can see how i have Catalyst Center working and showing my video card!! But why am i not getting direct rendering and why is it using MESA still?

the error i notice is:

Xlib : Extension "XFree86-DRI" missing on display ":0.0"

not sure if thats whats causing this but any help would be great. I will have to get my Xorg.conf file and show it but im currently at work. I have another person look at my xorg and he said its fine, just as i assumed but i still will post it.


If any other information is needed please say.

My Main PC

Feisty 7.04 (32 bit)
Athlong 64 3000+
3 GB DDR
80 GB X 2 SATA
Asus K8V-SE Deluxe
ATI x1650 512 DDR2
Pci Lan card (linksys)
dual 19 inch widesreens (1440x900)

---

### Post by bigpetey44 on 2007-09-21
Bump with new info

I used the restricted drivers manager and installed the driver...setup dual monitors however there is now some graphic imperfections. Im happy thought because i do have direct rendering and my correct ati drivers installed, however there are some graphic tears and drags...


here is a picture of it on pclinuxos that i had teh same problem.

[http://i130.photobucket.com/albums/p247/bigpetey44/snapshot1-1.png](http://i130.photobucket.com/albums/p247/bigpetey44/snapshot1-1.png)

i will get more pics to show whats going on. Anyone know if this can be fixed by editing anything in Xorg.conf??

Anyone have any suggestions?? Is it a opengl problem or something, or does my card just suck??

---

