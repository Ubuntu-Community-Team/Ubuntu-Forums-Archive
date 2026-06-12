---
title: "Tv-out on Radeon Mobility 9700"
date: 2005-08-13
forum: Hardware &amp; Laptops
---

### Post by johannes on 2005-08-13
Hi. I have a laptop that uses the Radeon Mobility 9700 card. I have followed the  [HowTo: Ati FGLRX 8.14.13](http://www.ubuntuforums.org/showthread.php?t=32495) and get around 2000 fps in Glxgears which is great.

My problem is that I can't get tv-out to work. When I connect the TV all I get is some insane monochrome flickering, which probably shows that the tv-out port works, but is not configured. I have tried to run fglrxconfig several times with different options but it makes no difference as I'm probably doing something wrong.

I have also tried the package "atitvout", but it says "VBE call failed" even though the vbe module is loaded in X. I guess it simply doesn't support this card.

Has anyone gotten tv-out to work with this card? If so, please explain how you did. Any help will of course be appreciated.

I have attached my xorg.conf.

---

### Post by s_p_a_r_k_y on 2005-08-13
hi,

in my past experiences with S-video, you have to shut down the PC and have the TV connected via s-video prior to bootup. It should be able to display everything until X loads. Once X loads it needs to know what devices to use so you should have an extra device section for your s-video out with appropriate resolutions and such.

Hope that helps...also make sureyou get the resolutions right, I believe you can damage old TVs if its to high or to low

---

### Post by johannes on 2005-08-14
I have tried that but it doesn't work since I can't even get the console text to show up on the TV... Thanks for trying to help though.

---

### Post by johannes on 2005-08-20
Somehow I got it to work, but at the cost of 3d acceleration. I installed the [latest ATI drivers](http://www.ubuntuforums.org/showthread.php?t=57743)  but when I restarted the computer I only got the Mesa drivers:

fglrxinfo:
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

TV-out works fine and I can live without openGL since I don't play a lot of games. The 3d program Maya I have installed seems to work so I'm happy with that.

---

### Post by johannes on 2005-09-11
One more follow up. I managed to install the latest ATI drivers, version 8.16.20 using  [this guide](http://www.ubuntuforums.org/showpost.php?p=297524&postcount=164). Now both 3d acceleration and tv-out works nice with practically no tweaking. :)

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

A problem though is that I have to lower the resolution on the LCD when I want to use the TV, otherwise the picture on the TV seems too big and is scrolling when I use the desktop. But thats no big deal.

I attached my xorg.conf if someone wonders how it's set up.

---

### Post by u-blunt-2 on 2005-12-01
> I managed to install the latest ATI drivers, version 8.16.20 using this guide. Now both 3d acceleration and tv-out works nice with practically no tweaking. 

You mention you got the 8.16.20 fglrx driver working, using the 8.14.13 guide ???

---

### Post by johannes on 2005-12-07
I simply installed the binary 8.16.20 driver from ATI's website. I don't know if they host it anymore, this was some time ago. I guess the latest should work also.

If I remember correctly, install the packages dependencies for the ubuntu fglrx package (but not fglrx itself). Mark it in synaptic and unmark again. Also install build-essential and the kernel headers.

---

