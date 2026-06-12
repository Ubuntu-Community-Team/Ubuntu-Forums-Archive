---
title: "Kensington trackball"
date: 2006-05-10
forum: Hardware &amp; Laptops
---

### Post by jerrybee on 2006-05-10
Do you know of configuration software for the Kensington Expert Mouse trackball ? I see that they have no driver s/w for Linux and have just asked them, via email, if they intend to provide same.  I'd like to be able to set up 3 of the 4 buttons to enable 'click', 'double-click', and 'right-click'.  Not the end of the world, but a convenience.

---

### Post by Sef on 2006-05-10
take a look here:

[http://saragossa.net/linux-tips/page.php?key=Auto-Mouse+Config]("http://saragossa.net/linux-tips/page.php?key=Auto-Mouse+Config")

---

### Post by jerrybee on 2006-05-14
Sef, do you use a Kensington Expert Mouse?  I tried the fix from the Web site your link took me to; the fix talked about 3 buttons, but in real-life the computer asked for input for 5 buttons.  The man page was no help either.  I need to be able to not only change which button does what, but also assign actions to buttons, and I haven't yet found such configuration info.  And Kensington came back saying I'd sent my request for info to the wrong office, so I replied to that email and haven't heard back from them yet (several days now).
    Anyway, thanks for the help.  At least I don't feel alone in this.

---

### Post by odelay on 2006-10-03
I also have a Kensington Trackball Expert Mouse that I'd like to get the top 2 buttons working on.  It's good not to feel alone.  ;)

---

### Post by dananimal on 2006-11-10
I am also hoping to configure Kensington trackballs to operate with Ubuntu. Both an "Expert Mouse" and an "Expert Mouse Pro".
Two buttons work fine but the other buttons would be really handy.
BTW The URI above to [www.saragossa.net](www.saragossa.net) doesn't work so I couldn't even try it.
;D

---

### Post by bgoody on 2006-11-10
Hi.  I have one of those and have it working somewhat.  Here is the relevent section of xorg.config.

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "Buttons" "7"
	Option	    "ZAxisMapping" "4 5"
EndSection

---

### Post by odelay on 2007-04-08
Thanks for the info **bgoody.**

That got all my buttons doing something...it's just that I don't know how to modify what that something is.  For example, I'd like to set my upper right button to close windows (CTRL + Q).  Do you have any idea how to do this?

---

### Post by sugarland2k on 2007-07-12
I use an Kensington Expert Mouse (trackball) on a KVM swith on my Kubuntu system and I need to get all my buttons and scroll ring working right.  Check out this post...

I will try this when I get home and post my results.

[http://ubuntuforums.org/showthread.php?t=448768](http://ubuntuforums.org/showthread.php?t=448768)

---

