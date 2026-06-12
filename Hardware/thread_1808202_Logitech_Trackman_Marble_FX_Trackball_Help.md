---
title: "Logitech Trackman Marble FX Trackball Help"
date: 2011-07-20
forum: Hardware
---

### Post by Cgenec on 2011-07-20
Hey hey.. I have an older Trackball a Logitech Trackman Marble FX.  I've had it for years now and just recently found the ball and plugged it into my "BOX" and it works ok with the right and left buttons, but there is no scrolling.  Is there a way to config the system to get this guy to work?  Alot of the other threads talk about the newer MARBLE mouse with USB connection.. and/or from older distro's.  
Im running Kubuntu 11.4
Track ball is a PS/2 mouse plug through a converter to make it USB (since I dont have a PS/2 plug on the computer) 

thanks
 [HERE]("http://www.logitech.com/en-us/support-downloads/downloads/trackballs/devices/3983") is the mouse

---

### Post by Cgenec on 2011-07-20
ok..so I figured it out all on my own. here are the steps in case any one wants to know...

1. in terminal ran   $ xev
in the little box in the corner of the screen, i kept hitting all the buttons on the mouse to determine which button did what.  I found that (Left click) is 1, (Right click) is 3 and the (middle) button was 2..

<NOTE> my little red button does nothing still, wont even register as a click in     xev

2. Downloaded gpointing-device-settings from the repositories. and ran the command.
I then selected (PS/2 Mouse), selected "use wheel emulation" button "2", selected "enable vertical scroll" and clicked <OK>

BOOM!!!  I have scrolling with my trackball!!!

HOPE THIS HELPS

---

### Post by tomek_wap on 2011-10-31
too bad it doesnt work for my trackman marble :(

---

### Post by pjhooker on 2012-12-14
Man you are wonderful!!!
It worked like a charm!!!
Thanks!

---

### Post by vector on 2013-10-30
This works, awesome... but on button 2 (which for my PS2 trackman marble FX is the right click). 
I still cant get it to work with the little red button. I went thru all the available buttons on the drop down. the little red one just does not seem to register.

any ideas?

---

### Post by smilz247 on 2014-01-02
Read in another forum that the red button identifies itself as button #8 even though there are only 4 buttons. [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/889292]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/889292")

---

