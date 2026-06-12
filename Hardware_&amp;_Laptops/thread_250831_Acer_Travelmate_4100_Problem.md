---
title: "Acer Travelmate 4100 Problem"
date: 2006-09-04
forum: Hardware &amp; Laptops
---

### Post by dan.erasmus on 2006-09-04
Hi All

I have an Acer Travelmate 4100 and i'm trying to load ubuntu for the first time. I have version 6.06, it only came with one CD. 

When i boot with the CD in the drive, i get to the selection screen. i then select "Start or install Ubuntu" and I add the following to the end of the boot options line >> (after the --)

"boot: live vga=771 noapci nolapci" (less the " sign)

the system then goes through the startup process and as far as i can see, everyting loads fine. all the components load with an "ok" next to it!

I then get a cursor flashing in the top left corner of the screen and the next thing the screen goes black, like it is off. I then hear music playing, like it is starting up, and that is it! no grahics, no nothing. if i press "ctrl" "alt" "f1" i get to a text interface. (i assume that means ubuntu started fine, is running, but is not displaying anything) if i then try to restart gnome using the "sudo /etc/init.d/gdm restart" i get an "ok" for the stopping of gnome, but a fail for the starting of gnome. (remember this is all from the Live CD boot)

If I do the same thing with the "Start Ubuntu in safe graphics mode" setting and add the same line, I get the flashing cursor again and then a blue screen (excuse the pun) saying: 

"Failed to start the x server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the x server output to diagnose the problem?"

if i have a look at the log file, the only problem that I see is a line that says the following:
=========================================
(EE) VESA(0): Set VBE Mode Failed!

Fatal server error:
AddScreen/ScreenInit failed for driver 0
=========================================

the above is the only error in the file.

are the two problems the same thing, and am i only able to see the problem in safe mode, or are they different problems? and how do I go about fixing the problems.

I hope i have given enough information for someone to help me and that it all makes sense.

regards,

dan

---

### Post by dan.erasmus on 2006-09-05
I have also tried to ](*,)  and this also does not work!!!

So if there are any x server experts out there, please give me some advice!

thanks,

Dan

---

### Post by arkangel on 2006-09-05
do you have an Ati Xnnnn card ?

if so , after the  live CD  put you in the console (if not press alt+F1)
go to  /etc/X11 and  edit  (vi or  nano )  xorg.conf  look for  device section and add these lines 
     $ Option "BusType" "PCIE"
     $ Option "MonitorLayout" "LVDS, NONE"

then  type in the console  
startx 

i hope it helps

---

### Post by dan.erasmus on 2006-09-05
thanks for the reply!!

when i do the above, i get the following error message:

=================================================
xauth: creating new authority file /home/ubuntu/ .serverauth.6599

Fatal server error:
Server is already active for display 0
              If the server is no longer running, remove /tmp/.X0-lock
              and start again.
=================================================

i would appreciate it if you coule help me out on this!!

thanks

dan

---

### Post by arkangel on 2006-09-05
X is still running 

try the following  crtl+alt+F7  and if you see only a  black screen with no other sign, force restanting (with he change you already did in xorg.conf )

for restanting X , crtl+alt+bkspc , when you are in this black screen  

you can always go back to you console wth crtl+alt+F1

---

### Post by dan.erasmus on 2006-09-05
ok, now i am getting the following error when i do as you described to force a restart of x

it says:
====================================================
Parse error on line 95 of section Device in file /etc/X11/xorg.conf
                       "BusType" is not a valid keyword in this section.
(EE) Problem parsing the config file.
(EE) Error parsing the config file.

Fatal server error:
no screens found

XIO: fatal IO error 104 (connection reset by peer) on X server ":0.0"
       after 0 requests (0 known processed) with 0 events remaining.
=====================================================

---

### Post by dan.erasmus on 2006-09-05
================================================== ==
Parse error on line 95 of section Device in file /etc/X11/xorg.conf
"BusType" is not a valid keyword in this section.
(EE) Problem parsing the config file.
(EE) Error parsing the config file.

Fatal server error:
no screens found

XIO: fatal IO error 104 (connection reset by peer) on X server ":0.0"
after 0 requests (0 known processed) with 0 events remaining.
================================================== ===

---

### Post by dan.erasmus on 2006-09-06
i have edited my xorg.conf file to look similar to the one in the post [http://www.ubuntuforums.org/showthread.php?t=251853](http://www.ubuntuforums.org/showthread.php?t=251853)

mainly i changed the "monitor" identifier to "Laptop Monitor" and the "screen" monitor to "laptop monitor" but now i am getting the following error when i try to start x

===================================================
(EE) VESA(0): Set VBE Mode failed!

Fatal server error:
AddScreen/Screeninit failed for driver 0

XIO:    fatal IO error 104 (connection reset by peer) on x server ":0.0"
          after 0 requests (0 known processed) with 0 events remaining.
===================================================

---

### Post by arkangel on 2006-09-06
could you tell me which graphic card do you have ?
reading the first post  you want to test the live CD ,  try again but  with the second option, when booting  the cd something like "starting in grapich save mode "

---

### Post by dan.erasmus on 2006-09-06
the graphics card is an:
ATI Mobility Radeon x700 PCI Express with 64MB VRAM
sorry, i should have added that in the first place!!

well, i want to install ubuntu on this laptop for testing purposes. I am trying to boot with the live CD/DVD to try and get to a point where I can install ubuntu. i will only install ubuntu if I am sure i can run ubuntu on the laptop, that is why i was trying to run the live CD.

is it easier to get an installed version working than the live cd version?

when i start the live CD in safe graphics mode, i still get the blue screen saying: 
"Failed to start the x server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the x server output to diagnose the problem?"

the error in the log file is the same one as below
=========================================
(EE) VESA(0): Set VBE Mode Failed!

Fatal server error:
AddScreen/ScreenInit failed for driver 0
=========================================

---

### Post by Makoshark on 2007-03-06
I have the same problem,how did you resolve it????HELP ME PLEASE!!!!!!!!!I'm going crazy!I've tried also the [solution]("http://wiki.x.org/wiki/FAQErrorMessages?highlight=%28server%29%7C%28is%29%7C%28no%29%7C%28longer%29%7C%28running%2C%29%7C%28remove%29%7C%28/tmp/.X0-lock%29%7C%28If%29%7C%28the%29#head-53291ef0dec609149a02a69c47ca70e77b238fdf") of wiki.xorg but I can't install Ubuntu on my desktop...Do you know if there's some ubuntu/kubuntu distibution expecially for laptops???Thank you very much!

Daniele

---

