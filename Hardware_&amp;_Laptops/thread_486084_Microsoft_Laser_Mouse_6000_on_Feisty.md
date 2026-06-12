---
title: "Microsoft Laser Mouse 6000 on Feisty"
date: 2007-06-27
forum: Hardware &amp; Laptops
---

### Post by kitty500cat on 2007-06-27
Howdy, I'm new to the forum.  Nice to be here. :)

Anyway, I just bought an Acer TravelMate 3260 from Newegg and installed Feisty.  After using the touchpad awhile, I got sick of it and bought a Microsoft Laser  Mouse 6000 (5 button) as well.  Right- and left-clicking work fine, but the back/forward buttons don't wanna work in Ubuntu.

At first the left thumb button didn't work at all, or if it did, it had some unuseful function.  The right thumb button did the same as a right-click.  I forget if the scroll wheel worked in scrolling and clicking or not.

I was messing around with some settings and managed to screw something up so that the right and left thumb buttons don't work at all, and the scroll wheel controls back/forward in web browsing.  I'm not sure if it works in any other applications.

How do I configure my mouse so that I can scroll with the scroll wheel and browse the web using the back and forward (thumb) buttons?  I normally browse using Opera.

Thanks in advance!

Regards :)

---

### Post by rootkowski on 2007-06-27
Hello!

Not long ago I had to deal with the very same problem. What you need to do is to edit the xorg.conf file (to be found in /etc/X11/xorg.conf). How to do that you can find here: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Activate_side-mouse-buttons_in_FireFox]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Activate_side-mouse-buttons_in_FireFox")

It's pretty simple (even I managed ;-) ) Though I had to adjust that a bit (and I also have MS Laser Mouse 6000). In my xorg.conf the code looks like this:
[FONT="Courier New"][SIZE="2"]Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
    Option         "Buttons" "7"
    Option         "ButtonMapping" "1 2 3 7 6"
EndSection[/SIZE][/FONT]

The thing is you might have to play with the numbers of the buttons to get it work the way you like (the way it's written on that site you'll be switching web pages with the scroll wheel).

I hope it's helpful what I wrote. Good luck!

---

### Post by kitty500cat on 2007-06-27
Thanks a lot mate. :)

It worked, except that the back and forward buttons were switched for my preferences.  I did a little configuring with IMWheel, and it worked fine.  Thanks again, you're a star :KS

Regards :)

---

### Post by rootkowski on 2007-06-28
Thank you a lot! I'm glad I could help. :-)

Thanks to your post I got inspired to install IMWheel too and after some playing around with button numbers it works great for me now.

Greets!

---

### Post by kitty500cat on 2007-06-28
I think the only problem for me was that buttons 6 and 7 were switched.  I think all it took was
```
imwheel --buttons -b 67
```
or something like that, that simply switched buttons 6 & 7.

Regards :)

---

