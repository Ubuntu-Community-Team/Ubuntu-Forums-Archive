---
title: "Multi-Button mouse configuration 11.04"
date: 2011-06-24
forum: Hardware
---

### Post by androssofer on 2011-06-24
Hi,

I'm running 11.04 with unity. and have a logitech m705 mouse, which has a few extra buttons. on my mac i can link them into expose and spaces etc... and i'd love to do the same in ubuntu with the desktop wall etc...

i read this article:

[https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)

which was gd. but the example at the bottom is quite lacking... with no explanation. Would anyone be able to help me? for example how could i make 1 of the extra buttons(like the forward and/or back button) bring up the desktop selector (desktop wall)..? or wer I could find more examples of how to change the mouse buttons and i could play around with the settings myself...?

Thanks

---

### Post by androssofer on 2011-06-28
further research into the subject found this article that helped greatly! hope its useful to others lookin to jaxx up their mouse :-)

[http://www.ghacks.net/2011/06/28/how-to-customize-extra-mouse-buttons-in-linux/](http://www.ghacks.net/2011/06/28/how-to-customize-extra-mouse-buttons-in-linux/)

---

### Post by rabarrett on 2012-06-10
I'm new to ubuntu (and linux).

Background:
I just installed and one of the first things I wanted to do was get my mouse going properly.  I have two MX 610 cordless mice from Logitech.  Normally I like to reconfigure the browser forward and back buttons to ctrl-w (close tab) and ctrl- (just ctrl so I can use it to control-click to open in a new tab without using keyboard).  I also adjust the scroll wheel to scroll a whole page for each click (become pagedown).

The other buttons I've thought about using to send me to the desktop or launch an app.

Right now it does nothing.


Problem:
I tried finding the "btnx" app androssofer linked to, but it's not in the ubuntu 12.04 software center.  Then I tried to terminal it with "sudo apt-get install btnx" but was told "Unable to locate package btnx."

Is there another program that can do this OR a way I can get btnx?

Help much appreciated,

Richard

---

### Post by Justin Buser on 2012-10-30
Logitech G700 with imwheel installed and back/forward buttons set to Generic Button in setpoint

In /etc/X11/xorg.conf in the mouse section:

```
Option         "Buttons" "1 2 3 4 5 6 7 8 9"
Option         "ZAxisMapping" "4 5"
```

in /etc/X11/imwheel/startup.conf:

```
IMWHEEL_START=1
IMWHEEL_PARAMS='-b "0 0 0 0 6 7"'
```

to make back and forward buttons work in web browsers

---

