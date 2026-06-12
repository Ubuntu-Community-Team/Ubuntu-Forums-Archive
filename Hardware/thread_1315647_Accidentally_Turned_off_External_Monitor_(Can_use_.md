---
title: "Accidentally Turned off External Monitor (Can use command line)"
date: 2009-11-05
forum: Hardware
---

### Post by cowcow1212 on 2009-11-05
Hello guys, I have a problem with my setup. The main screen, the original flip-down LCD screen, display 0 is broken. 

When I was adjusting my settings on the desktop screen, I accidentally turned off my LCD screen. I looked over the log files in /var/log folders, and it seems that the screen is registering (which I see when it is booting up), but when it gets to Kbuntu's welcome screen it shuts it off. 

The log file var/log/Xorg.1.log states event 11 detected, and does nothing more which makes me think that this event is the source of the problem. 

I have tried xrandr --output VGA-0 which then states DISPLAY=0.1 cannot be opened. 

I have also tried shutting down kdm (sudo /etc/init.d/kdm stop), then tried reconfiguring xorg by, sudo dpkg-reconfigure -phigh xorg; and then tried to restart kdm by sudo /etc/init.d/kdm start . 

xfix does not work either. 

When I have tried to initiate my drivers on xorg, using aticonfig --initiate -v, I get an error stating a segmentation fault had occurred.

Does anyone know how to force the monitor open in X7 server? 

I know it has something to do with the Default Screen, but changing xorg manually at the level of even /etc/X11/xorg.conf does not change this monitor from being off! According to the manual, this is the highest level xorg works from, and since it is being found and initialized prior to kdm starting, I think this is an issue of kdm.  

Any ideas? Thanks for your time guys.

---

