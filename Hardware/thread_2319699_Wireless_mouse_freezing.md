---
title: "Wireless mouse freezing"
date: 2016-04-06
forum: Hardware
---

### Post by t-tomislav on 2016-04-06
Hello everyone.
I have a Logitech NX80 wireless mouse.
It becomes unresponsive after not moving for a few seconds. Moving and clicking doesn't work - i have to move it quite a bit, to get it to work again. Meanwhile, touch pad works OK.
Batteries are OK - not only that i unpacked them recently, I also dual boot into windows, and there I don't experience this behavior.

Does anyone have this kind of a problem, and please how did you solve it?

---

### Post by RobGoss on 2016-04-07
Hello and welcome, This is not a fix but I just wanted to share my experience with this issue. When I first install Ubuntu 14.04 I was having problems with my wireless mouse also but after trying to trouble shoot what the problem was I decided to use a wired mouse instead, after a few updates and my system became a bit more stable I then started using my wireless mouse again and all seem ok. Maybe it's something in one of the updates that is needed I'm not really sure.

---

### Post by scpatl4now on 2016-04-07
I am using a WIRED usb mouse and having the same issue.  It works fine for a while then will stop.  I cannot click or get it to move.  A strange thing I noticed was if I move the page with up/down arrows, the mouse curser will change depending what is under it.  Unplugging and replugging the mouse makes it work again, but this is hetting to be a pain.  I have also noticed that the tracking light under the mouse will go out as well or sometimes start to blink more slowly (both disable the mouse).  This just started happening the last couple of days on 14.04.  What is the best way to go about troubleshooting?

---

### Post by RobGoss on 2016-04-07
Have you recently updates your Ubuntu system? if not try updating it to see if that will fix any issues you may be having

Also here's a post that might shed some light on your problem
[http://askubuntu.com/questions/506673/usb-mouse-not-working-after-unplug-plug-in-14-04](http://askubuntu.com/questions/506673/usb-mouse-not-working-after-unplug-plug-in-14-04)

---

### Post by him610 on 2016-04-07
Hello.
FWIW, I too have a Logitech wireless mouse (model M325), and a Logitech wireless keyboard Model K400r) both paired with one Logitech Unifying Receiver. I have recently upgraded to Xubuntu 16.04, and since updated as recently as today. My wireless mouse and keyboard have never failed to operate except when initially modifying BIOS settings.
On the newer models of the Logitech Unifying Receiver, a USB extension bout 1-1/2 inches long is included. I think it was included to prevent RFI from the computer interfering with R/T of the receiver.

---

### Post by Alex_Metivier on 2016-04-08
The best way would be for you to test the mouse on a different computer, if it still does not work the it is the mouse it self that does not work, if it does work the try another usb port on your computer if you have one. if it works on a different port then it would just be that port that is malfunctioning

---

### Post by scpatl4now on 2016-04-08
I have tried my mouse on another computer and have no problems.  I have used 2 different usb ports (front side and rear) on this PC and the same behaviour eventually happens.  The light on the bottom of the mouse flickers or goes out and mouse freezes or becomes sporadic or both.

---

### Post by scpatl4now on 2016-04-08
This fixed my issue 
[http://ubuntuforums.org/showthread.php?t=2226559&page=3](http://ubuntuforums.org/showthread.php?t=2226559&page=3)
My usb ports were set to auto suspend.  I used powertop (explanation in above link) under tunable and set them to not do that (although I might have to repeat after reboot)

---

### Post by RobGoss on 2016-04-09
Glad to see you got it sorted out, if you don't mind can you mark this thread as solved using the **Thread Tool tab,** at the top of this post. Thank you

---

