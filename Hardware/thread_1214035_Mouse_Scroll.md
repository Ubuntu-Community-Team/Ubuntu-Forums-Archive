---
title: "Mouse Scroll"
date: 2009-07-15
forum: Hardware
---

### Post by gzigoris on 2009-07-15
[FONT=Arial Black][COLOR=black][SIZE=1]I have just installed Ubuntu on a clean HDD and the installation went great but I am having problems with my mouse scroll wheel. Every click of the scroll wheel causes about 15 lines to advance. WOW It's hard to use and I don't enjoy the up and down arrows on the sidebar. Is there a solution to this? My mouse is a Wireless Laser mouse 5000. I think in Windows I get 3 lines for each click of the wheel.  Makes the scrolling wheel extremely difficult to use. HELP!

George](*,)
[/SIZE][/COLOR][/FONT]

---

### Post by gianluca.pettinello on 2009-07-15
You can modify your xorg.conf

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo gedit /etc/X11/xorg.conf

you add

Section "InputDevice"
        Identifier "Configured Mouse"
        Driver "mouse"
        Option "Protocol"    "auto"
        Option "Device"     "[FONT=Courier New][COLOR=#0000ff]/dev/input/mice[/COLOR][/FONT]"
        Option "Buttons"     "5"
        Option "ZAxisMapping"  "4 5"
        Option "CorePointer"
        Option "SendCoreEvents" "true"
       EndSection

And then you restart your session

Gianluca

---

### Post by gzigoris on 2009-07-15
Thanks for the information. Drove me crazy trying terminal mode as a Noob. I input everything without a problem but it didn't seem to fix the scrolling. Are there parameters that I can play with to see if it will change. When I use the wheel scroll it still gets wild and moves too many lines at once.

Being new I am not sure if I am doing this correctly.

George:lolflag:

---

