---
title: "Help permanently changing screen resolution"
date: 2010-03-07
forum: Hardware
---

### Post by kinton on 2010-03-07
Hi.

I have the code to type in to the terminal which will change my screen resolution to its best setting. 

xrandr --newmode "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
xrandr --addmode VGA-0 1680x1050_60.00
xrandr --output VGA-0 --mode 1680x1050_60.00
However, every time I restart the PC it goes back to its old setting! :frown: 
I tried to follow the guide on this website  [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) where it suggests putting the xrandr code in the /etc/gdm/Init/Default file but it still boots up with the old resolution.

Please help!

P.S. My PC only has one user - im not sure if this should affect the method I use or not

---

### Post by lyall on 2010-03-07
read this it might help for setting us ATI video cards
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide")

good luck and have fun learning

---

### Post by kinton on 2010-03-08
Hey i followed the guide and all the correct screens came up, and it indicated that the packages had been installed and were up to date...

...however after a reboot its still the wrong resolution!

P.S. I forgot to mention this before but I dont have the video card driver installed because by default it outputs at a resolution too high meaning I cant use the PC

---

### Post by kinton on 2010-03-11
Still no help?

---

### Post by robnils on 2010-03-16
I'm having the same problem, gonna try this, might help: [http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

---

### Post by kinton on 2010-03-16
Ok, I tried that once but it wouldnt work

Please let me know how you get on with that :)

---

### Post by mvelte54 on 2011-07-28
> **robnils said:**
> I'm having the same problem, gonna try this, might help: [http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

I too am having the same problem. If you read the "X/Config/Resolution - Ubuntu Wiki" they say that the particular code you are attempting will not work. 

"https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution"

**Important Note** Be careful with your **X** if you _copy_ from a website like what you see below otherwise you will get this nice message.  **xrandr: cannot find mode 1024×768** 
[http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html](http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html) 
This website uses some kind of mini **x** which does not work. 
(Read the wrong font)

Look in the section:
[B]Three methods to setup (about half way down)
[/B]
Also in the comments section on the Ubuntu geek site some wrote that they needed to write VGA-1 rather than VGA1 in order to get it to work.

 Now I haven't tried this but I am about to only I'm going to do it the old fashioned way and type it in rather than cut and paste which I'm sure many of us are guilty of. Good luck to all.

---

