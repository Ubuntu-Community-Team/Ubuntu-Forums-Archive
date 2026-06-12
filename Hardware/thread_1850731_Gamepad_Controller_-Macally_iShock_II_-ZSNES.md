---
title: "Gamepad Controller -Macally iShock II -ZSNES"
date: 2011-09-27
forum: Hardware
---

### Post by Stoppelmonster on 2011-09-27
Hi, I need help setting up a Macally iShock II to play games with ZSNES. So far I used some tips I found in [this thread]("http://ubuntuforums.org/archive/index.php/t-1583045.html"). From there I added a 50-joystick.conf that read like this:

> 
Section "InputClass"
Identifier "joystick catchall"
MatchIsJoystick "on"
MatchDevicePath "/dev/bus/usb/004/001*"
Driver "joystick"
 Option "StartKeysEnabled" "False"
    Option "StartMouseEnabled" "False"

EndSection

ZSNES now sees the device but my control is limited, and the buttons do not work. 

Any suggestions would be greatly appreciated. 


-Ubuntu 11.04

---

