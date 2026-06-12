---
title: "Where did my mouse wheel go?"
date: 2005-03-20
forum: Hardware &amp; Laptops
---

### Post by Ecgtheow on 2005-03-20
Hey folks,

My mouse wheel died a few days ago when  X stopped working  from the update.  After a fevered dist-upgrade X worked again, but after that, no wheel.  It's a generic, and I mean generic, compusa travel usb optical plugged into my Compaq presario 2140US LT.

I can't remember if I had to configure that sucker when I installed Hoary a few weeks ago or not.Seems to me it was not, as that is the kind of thing I would have remembered, cause that's a pet peeve.

Anyhow, thanks.

Ecg

---

### Post by ubuntu_demon on 2005-03-20
[QUOTE=Ecgtheow]Hey folks,

My mouse wheel died a few days ago when  X stopped working  from the update.  After a fevered dist-upgrade X worked again, but after that, no wheel.  It's a generic, and I mean generic, compusa travel usb optical plugged into my Compaq presario 2140US LT.

I can't remember if I had to configure that sucker when I installed Hoary a few weeks ago or not.Seems to me it was not, as that is the kind of thing I would have remembered, cause that's a pet peeve.

Anyhow, thanks.

Ecg[/QUOTE]
 I had the same problem after I reconfigured my xorg server.

try adding this line in your mouse section of xorg if they are not there (worked for me and I have a logitech dual optical). This option was the one that did it for me I believe :

    Option          "ZAxisMapping"          "4 5"


you can also fiddle around with enabling/disabling 3 button emulation:

    Option          "Emulate3Buttons"       "true"

or try setting the number of mouse buttons like :

Option "Buttons" "5"

If that doesn't work try changing your mouse protocol to something else ... maybe auto,imPS/2 or compaq (if that protocol exists). I have an USB logitech dual optical but this is the protocol I use:

    Option          "Protocol"              "ImPS/2"

see also this thread :
[http://www.linuxquestions.org/questions/history/289662](http://www.linuxquestions.org/questions/history/289662)

---

### Post by Ecgtheow on 2005-03-21
Thanks, your fix was right on the money.  

However, I dumped Hoary and reinstalled it last night anyway, cause I hosed up a few other things whileI was playing with it.  So now it works again.  I also found a k7 kernel which I am using, but I can't tell if it's any faster than 686.

Thanks again!

what a great distro and a great community.

Ecg

---

### Post by c_dog on 2005-03-22
And if you have one of those mice with those left and right side buttons. You go with:

Option "Buttons" "7"
Option "ZAxisMapping" "6 7"

in your xorg.conf

You may need run the xev utility to see which buttons are doing what and use xmodmap to swap a few buttons. A script like this placed in your /etc/X11/xinit/xinitrc.d folder can do this automatically at startx

#! /bin/sh
xmodmap -e "pointer = 1 2 3 6 7 4 5"

 
Then you use the right and left side buttons to "forward" and "back" browser pages or scroll   -pan right and left on a page.

---

