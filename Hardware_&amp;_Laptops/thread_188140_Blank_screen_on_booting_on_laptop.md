---
title: "Blank screen on booting on laptop"
date: 2006-06-03
forum: Hardware &amp; Laptops
---

### Post by Dfects on 2006-06-03
Hey :)

I just tryed to boot from the dapper 6.06 cd on my laptop (acer 5020 / 5024). I see the initial booting screen, but just before the ubuntu music plays as it boots the screen goes completely blank. I've not even got to install dapper yet, as i can't see the desktop to go through the install!

I've tryed pressing alt + shift + f1 to get the console and reconfiguring xserver but i'm not sure how to refresh it and get back to gnome? not sure if this will even help!

I'm a bit new to all this, the laptops native res is 1280x800@60 and its got an ATI x700 gpu. I didn't wanna install it just yet as i'm working hard on a piece of software which needs visual studio... i just wanted test out the live cd

---

### Post by mihai.ile on 2006-06-04
As I explained on this page about my Acer ( [https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire1694WLMi](https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire1694WLMi) )
> 
To make the monitor display anything but the blank screen after install i had to add this line in Section "Device":


Section "Device" 
[B]      Option "MonitorLayout" "LVDS,Auto"
[/B]

in the xorg.conf file.


---

### Post by ivotedforkodos on 2006-06-04
I am having similar symptoms, but I may have a different problem. 

First, I am using a Dell Inspiron 1000, which was recently upgraded from Breezy to Dapper. The upgrade went smoothly, although it took me a while to get my wireless card working properly, but eventually I did. So everything was working as planned, and the last thing I remember doing was setting the automatic login (there is only one account on this machine). The next day, when I tried to start up, I got through the Ubuntu startup, but was left with a black screen and the default X cursor. 

* I edited /etc/gdm/gdm.conf-custom to remove automatic login, but that didn't help. 
* I read this: [http://www.ubuntuforums.org/showthread.php?t=121819](http://www.ubuntuforums.org/showthread.php?t=121819), and tried this: <sudo dpkg-reconfigure xserver-xorg> a few times, but that didn't help either.
* I read this: [http://www.linuxquestions.org/questions/showthread.php?t=374347](http://www.linuxquestions.org/questions/showthread.php?t=374347), but I wasn't having ownership issues. I deleted all the .gnome and .gconf folders, but that didn't help either. 

I don't see anything obvious in /var/log/messages, but then again I don't really know I'm looking for. I can exit X with Crtl-Alt-F1, but I'm kind of a noob and I'm not sure what else to do. When I try "gnome-session", I get a Gtk-WARNING **: cannot open display. 

I don't see why the video driver would be an issue since it worked fine before. To be clear, I was able to restart the machine several times AFTER upgrading to Dapper before the problem started. I **think** the last thing that I changed was setting the default login. Now I never make it to the login screen. 

Please help!

---

### Post by tseliot on 2006-06-05
[QUOTE=ivotedforkodos]I am having similar symptoms, but I may have a different problem. 

First, I am using a Dell Inspiron 1000, which was recently upgraded from Breezy to Dapper. The upgrade went smoothly, although it took me a while to get my wireless card working properly, but eventually I did. So everything was working as planned, and the last thing I remember doing was setting the automatic login (there is only one account on this machine). The next day, when I tried to start up, I got through the Ubuntu startup, but was left with a black screen and the default X cursor. 

* I edited /etc/gdm/gdm.conf-custom to remove automatic login, but that didn't help. 
* I read this: [http://www.ubuntuforums.org/showthread.php?t=121819](http://www.ubuntuforums.org/showthread.php?t=121819), and tried this: <sudo dpkg-reconfigure xserver-xorg> a few times, but that didn't help either.
* I read this: [http://www.linuxquestions.org/questions/showthread.php?t=374347](http://www.linuxquestions.org/questions/showthread.php?t=374347), but I wasn't having ownership issues. I deleted all the .gnome and .gconf folders, but that didn't help either. 

I don't see anything obvious in /var/log/messages, but then again I don't really know I'm looking for. I can exit X with Crtl-Alt-F1, but I'm kind of a noob and I'm not sure what else to do. When I try "gnome-session", I get a Gtk-WARNING **: cannot open display. 

I don't see why the video driver would be an issue since it worked fine before. To be clear, I was able to restart the machine several times AFTER upgrading to Dapper before the problem started. I **think** the last thing that I changed was setting the default login. Now I never make it to the login screen. 

Please help![/QUOTE]
try with this command:
```
sudo dpkg-reconfigure gdm
```
then
```
sudo dpkg-reconfigure xserver-xorg
```
and set the driver to "vesa"

then reboot by typing:
```
sudo reboot
```

---

### Post by ivotedforkodos on 2006-06-05
[QUOTE=tseliot]try with this command:
```
sudo dpkg-reconfigure gdm
```
then
```
sudo dpkg-reconfigure xserver-xorg
```
and set the driver to "vesa"

then reboot by typing:
```
sudo reboot
```[/QUOTE]

Yeah, I read that, and I did that. No luck. Any other ideas?

What does it mean to get the black screen with the default cursor? It sort of appears as though things are working, I just can't see them.

---

### Post by mihai.ile on 2006-06-05
did you try my solution? i also have ATI x700 on Acer1694wlmi and works just great
i just did ctrl+alt+f1 then 
$ sudo pico /ext/X11/xorg.conf 
and in the section part i adde the line
Option "MonitorLayout" "LVDS,Auto"
save and restart X and it works.

---

### Post by deadgobby on 2006-06-05
I read an artical in Distrowatch. See if this helps
[COLOR="Red"]I reported this bug and received a polite response from the developers. While waiting for a fix, I've found a reasonable workaround. I edited file /etc/X11/xorg.conf and replaced the "ati" driver with "vesa". The vesa driver works with just about any hardware, but it's a noticeably slow driver. I no longer experience crashes, but I can forget about playing PlanetPenguin-Racer (ppracer, formerly known as TuxRacer).[/COLOR]

---

### Post by ivotedforkodos on 2006-06-06
I tried all of that. After I added the "MonitorLayout" item in xorg.conf, I did briefly return to GNOME after I restarted X, but it was unstable (kept coming in and out), and when I restarted, I came back to the black screen. I have since been unable to get back to the desktop no matter what I try. 

The graphics chip comes up as Silicon Integrated Systems (SiS), for whatever that's worth. Does anyone have any more ideas? Can I reinstall X using the CD? How can I back up my data at this point? I tried accessing a USB drive via the command line but it would not mount automatically. 

Please help!

---

