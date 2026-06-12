---
title: "Acer Laptop drivers - best source?"
date: 2011-09-29
forum: Hardware
---

### Post by Denver Dave on 2011-09-29
I'm running ubuntu 11.04 on an Acer Aspire 7741 which seems to work very well. However, the webcam and touchpad work, but have limited functionality.  

The touch pad does not recognize the right scroll area

The webcam video quality is much worse under ubuntu 11.04 than with windows 7.

I'm suspecting I'm not using the best drivers.

I contacted Acer support and they were of no help identifying where to get Linux drivers - just responded, we only support Windows.

Am I possibly on the right track to improve the touch pad and webcam performance?  If so, what is the best source to get linux drivers for an Acer Aspire 7741 ?

Thank you for your help.

= = = = =
found this later:
Enabling touchpad clicking and edge scrolling in Squeeze 
[http://lovingthepenguin.blogspot.com/2010/10/enabling-touchpad-clicking-and-edge.html](http://lovingthepenguin.blogspot.com/2010/10/enabling-touchpad-clicking-and-edge.html)

Haven't goofed up too much today, updated and rebooting - will report back.
= = = = = = 

rebooted - the above approach either does not work with ubuntu 11.04 to get edge scrolling on my Acer Aspire's touch pad or I did the change incorrectly.

Section "InputClass"
        Identifier "touchpad catchall"
        Driver "synaptics"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
	Option "TapButton1" "1"
	Option "VertEdgeScroll" "1"
EndSection

Also tried this approach from the ubuntuforums. Couldn't get this to work either, but looks like on topic:
[http://ubuntuforums.org/showthread.php?t=886449](http://ubuntuforums.org/showthread.php?t=886449)

---

