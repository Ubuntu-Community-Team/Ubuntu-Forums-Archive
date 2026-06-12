---
title: "i cant find the video card driver for sis6351"
date: 2012-12-06
forum: Hardware
---

### Post by penghack on 2012-12-06
i'm new for linux and i cant find the driver for sis6351(or sis mirage 3 graphics?i get the name of 6351 from a chinese software named driver genius which can install drivers autoly on windows)

my monitor's resolution is 1440*900 and the standalone driver card is broken,so i have to use the on-board card,but i cant get the best resolution. 

and i have searched the forum and web for several days ,i get some posts may be similar to my problem,but i'm not sure..because i cant ensure my card's model :(...i try to download same drivers and install them,but not work,may i install the driver by a wrong way(i copy the .so file with other file to xx/lib dir and so so..)...and i cant completely understand those posts..
what's more,my english is not so good,sorry...

i get these info from cpu-z on windows7
mother board info:
model: 671T-M
chipset: sis 671/fx/dx/mx
southbridge: sis 968
graphic card info:
name:sis mirage 3 graphics

ubuntu 12.04 32bit
that's all,if you need more info,plz tell me how can i get the info.
much thanks!i really want to use the ubuntu!

---

### Post by penghack on 2012-12-06
by the way i've find these posts:
[http://ubuntuforums.org/showthread.php?t=842383](http://ubuntuforums.org/showthread.php?t=842383)
[https://sites.google.com/site/openlinuxmintsources/sis-671-mirage-3-graphics-cards-drivers](https://sites.google.com/site/openlinuxmintsources/sis-671-mirage-3-graphics-cards-drivers)
[http://ubuntuforums.org/showthread.php?t=1201268](http://ubuntuforums.org/showthread.php?t=1201268)
[http://ubuntuforums.org/showthread.php?t=958967&page=38](http://ubuntuforums.org/showthread.php?t=958967&page=38)
[http://ubuntuforums.org/showthread.php?t=1573218](http://ubuntuforums.org/showthread.php?t=1573218)
[http://ubuntuforums.org/archive/index.php/t-927219.html](http://ubuntuforums.org/archive/index.php/t-927219.html)

---

### Post by ibjsb4 on 2012-12-06
Hi penghack

I think the best answer is buy a new video card unless this is a laptop.

Anyhow, looks like [this link]("http://ubuntuforums.org/showthread.php?t=958967&page=38") provides the best answer, but it is for 10.04 and needs to be modified to work in a later release.  I have not had to do this before, but here's what I came up with.

```
sudo cp sis671_drv.* /usr/lib/xorg/modules/drivers/

sudo service lightdm stop

Switch to tty1 by pressing Ctrl+Alt+f1

sudo bash

Xorg -configure

service lightdm start

sudo mv xorg.conf.d.new /usr/share/X11/xorg.conf.d

sudo service lightdm restart

sudo bash

echo blacklist vga16fb > /etc/modprobe.d/blacklist-vga16fb.conf

update-initramfs -u

reboot
```I of course have no way to test this.  So this could be a fix or this could totally bork your system.

I would suggest waiting for others to comment on this before trying it on your system.

Edit:  Had a typo

---

### Post by penghack on 2012-12-06
thanks anyway,i'll try...i dont worry about the system,i can re-install it..haha..

---

