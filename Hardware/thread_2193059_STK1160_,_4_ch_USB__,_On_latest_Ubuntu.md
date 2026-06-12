---
title: "STK1160 , 4 ch USB  , On latest Ubuntu"
date: 2013-12-11
forum: Hardware
---

### Post by possimreddy on 2013-12-11
hi all
i have installed latest edition of Ubantu 13.04
i am trying to to use 4ch USB DVR (Easy Cap)
lsusb says

Bus 002 Device 003: ID 05e1:0408 Syntek Semiconductor Co., Ltd STK1160 Video Capture Device
input survalence camera (CVBS)
if i run the follwing command 
mplayer tv:// -tv driver=v4l2:norm=PAL:width=720:height=576:outfmt=uyvy:device=/dev/video0:input=1:fps=25 -vf pp=lb -aspect 16:9 -ao sdl -vo sdl
[U][B]
End Result Green Screen[/B][/U]

[http://easycapdc60.sourceforge.net/](http://easycapdc60.sourceforge.net/)
the above link says the project is closed 
as the drivers are included in the kernal

please suggest every search online leads me to a dead end

i have tried different input options

---

### Post by j-willson on 2014-03-28
Bump

Can anybody help on this one, as I too need a driver for this.

---

