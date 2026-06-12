---
title: "Xorg + Logitech mx518 (forward/back)"
date: 2008-01-10
forum: Hardware &amp; Laptops
---

### Post by harold4 on 2008-01-10
I've searched for a week, literally trying every config that was posted as working to no avail.  

Everything but the back/forward buttons currently work.  Even the +- resolution buttons are working as expected.  In Dapper I had a config that worked perfectly, but that same config no longer works.

Does anyone have a working config for the Logitech mx518?  Thanks in advance.

---

### Post by EXCiD3 on 2008-01-10
Have you tried: [http://ubuntuforums.org/showthread.php?t=219894&highlight=logitech+how](http://ubuntuforums.org/showthread.php?t=219894&highlight=logitech+how)

I have used it with my MX518 and it works great. However I noticed that forward/backward do NOT work with nautilus, yet they work fine with Firefox.

---

### Post by harold4 on 2008-01-11
Tried it again just to make sure.  It seems what worked for Dapper no longer works in Gusty.

---

### Post by EXCiD3 on 2008-01-11
Try using Feisty. It works much better than Gutsy :D

---

### Post by harold4 on 2008-01-13
A buddy of mine is still on Dapper for a bunch of small reasons :-P

There has to be a way... I"m determined to find it.

---

### Post by EXCiD3 on 2008-01-13
Haha, post your xorg.conf for us to look at.

---

### Post by hyperq on 2008-02-06
I got the side mouse buttons on my Logitech MX518 working in Firefox. I am using the "evdev" driver, not the "mouse" driver. I am using Kubuntu 7.10 Gutsy, which already has the package "xserver-xorg-input-evdev" installed by default.

Simply change the mouse section of your /etc/X11/xorg.conf to this:

[HTML]
Section "InputDevice"
       Identifier      "Configured Mouse"
       Driver          "evdev"
       Option          "CorePointer"
       Option          "Buttons"       "7"
       Option          "ZAxisMapping"  "4 5"
       Option          "ButtonMapping" "1 2 3 6 7"
       Option          "Name"  "Logitech USB-PS/2 Optical Mouse"
EndSection
[/HTML]

---

### Post by mohbana on 2008-02-12
> **hyperq said:**
> I got the side mouse buttons on my Logitech MX518 working in Firefox. I am using the "evdev" driver, not the "mouse" driver. I am using Kubuntu 7.10 Gutsy, which already has the package "xserver-xorg-input-evdev" installed by default.

Simply change the mouse section of your /etc/X11/xorg.conf to this:

[HTML]
Section "InputDevice"
       Identifier      "Configured Mouse"
       Driver          "evdev"
       Option          "CorePointer"
       Option          "Buttons"       "7"
       Option          "ZAxisMapping"  "4 5"
       Option          "ButtonMapping" "1 2 3 6 7"
       Option          "Name"  "Logitech USB-PS/2 Optical Mouse"
EndSection
[/HTML]

I'll confirm if this works for me later.  Yes this works for me too.

---

### Post by JPotter on 2008-02-13
> **hyperq said:**
> I got the side mouse buttons on my Logitech MX518 working in Firefox. I am using the "evdev" driver, not the "mouse" driver. I am using Kubuntu 7.10 Gutsy, which already has the package "xserver-xorg-input-evdev" installed by default.

Simply change the mouse section of your /etc/X11/xorg.conf to this:

[HTML]
Section "InputDevice"
       Identifier      "Configured Mouse"
       Driver          "evdev"
       Option          "CorePointer"
       Option          "Buttons"       "7"
       Option          "ZAxisMapping"  "4 5"
       Option          "ButtonMapping" "1 2 3 6 7"
       Option          "Name"  "Logitech USB-PS/2 Optical Mouse"
EndSection
[/HTML]

I can confirm, this works where every other change I tried (there were several) broke X.

Thanks!

---

### Post by SamSlater on 2008-04-11
After looking -and trying- about 5 different ways to get my MX518's thumb-buttons working, from other threads on the subject, this is the only one that worked AND DIDN'T BREAK MY GRAPHICS.

Thanks!!!

=D>

---

### Post by oddworld on 2008-04-26
My mx518 works in Hardy as default in firefox.
I did not have to change anything at all.
Does not work in Nautilus though - o well.

---

### Post by |moon| on 2008-04-30
Alright, my mouse works fine in firefox forward back buttons and everything else, and it has worked fine from the start with the latest hardy version, however when I go to use the forward and back buttons in Opera they don't work.  When I start opera using -debugmouse it maps the side buttons as buttons 8 and 9 whereas I think they should be 6 and 7, how do I fix this?

---

