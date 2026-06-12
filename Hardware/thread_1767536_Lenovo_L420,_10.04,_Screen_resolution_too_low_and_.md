---
title: "Lenovo L420, 10.04, Screen resolution too low and ugly graphics"
date: 2011-05-25
forum: Hardware
---

### Post by rokob on 2011-05-25
My problem is that the screen resolution is quite low and the graphics  just don't look smooth. It sort of looks like my old CRT monitor from  when I was about 10 years old. There is no xorg.conf file where it should be. Should I just write my own xorg.conf file  or is there a more intelligent way to go about fixing this issue? Following is the basic information and commands that I tried.

$ xrandr
Screen 0: minimum 1024 x 768, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       61.0* 

There is not /etc/X11/xorg.conf file and when I run the command:
$ sudo dpkg-reconfigure xserver-xorg

nothing happens and no xorg.conf file is created. The command:
$ Xorg -configre

gives this error:

Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.

So I presume I have to run this from the tty. However, I am a little new to Ubuntu, I was used to working mostly on the console and typing startx to get into X11. When I call /etc/init.d/gdm stop, I am not sent to the console but rather to a blank screen where I can type but nothing happens.

$ lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:0126] (rev 09)

I am pretty sure this is just the built-in standard Intel graphics.

---

### Post by Pazit on 2011-05-25
Hi rokob,

 I think you can find your way out by using the link below:
 [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by rokob on 2011-05-26
Nothing on the linked page seems to rectify the problem. Adding modes with xrandr only results in having the option to switch to that mode, but it won't actually make the switch.

Basically, I am stuck in safe graphics mode. I tried updating the intel driver but that didn't do anything. Should I move to a newer kernel?

$ uname -a
Linux betty 2.6.32-31-generic #61-Ubuntu SMP Fri Apr 8 18:24:35 UTC 2011 i686 GNU/Linux

---

