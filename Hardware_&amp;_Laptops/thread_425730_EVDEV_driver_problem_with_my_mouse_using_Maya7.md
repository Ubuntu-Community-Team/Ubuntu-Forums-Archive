---
title: "EVDEV driver problem with my mouse using Maya7"
date: 2007-04-27
forum: Hardware &amp; Laptops
---

### Post by eagle0691 on 2007-04-27
I got a Logitech mouse with two extra key in middle button, left and right. after I using the evdev driver I can use the two key now, I xmodmap the right side extra key to middle button, that useful, but the problem is , 

evdev driver the extra key as continuous key if you click it a while.  this cause a terrible crash in Maya, how could I modify it to a common middle key?  not a continuous click?  thanks !

---

### Post by justaguynpc on 2007-04-27
Can you give me some insight on how I could use evdev with my logitech mx revolution?  (Maybe?)

Cheers

---

### Post by eagle0691 on 2007-04-27
sure, first to install the driver :sudo apt-get install xserver-xorg-input-evdev

then:cat /proc/bus/input/devices , this will show a list, find that
 "I: Bus=0003 Vendor=046d Product=c040 Version=0110
N: Name=[COLOR="Red"]"Logitech USB-PS/2 Optical Mouse"[/COLOR]
P: Phys=usb-0000:00:02.0-2/input0
S: Sysfs=/class/input/input2
H: Handlers=mouse1[COLOR="Red"] event2[/COLOR] ts1 "
get the "event2" some like this, check out your event* ?

then backup your xorg.conf   ,  modify the mouse section, like this
"Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
[COLOR="Red"]    Driver         "evdev"[/COLOR]    #here to change the driver to evdev
    Option         "Protocol" "auto"
[COLOR="Red"]    Option         "Device" "/dev/input/event2"[/COLOR]  # and here set to your event
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection"

then restartx , in terminal: xev, click all the buttons in the window. all the buttons could work now, I use xmodmap to change the right extra button to middle butt (xmodmap -e "pointer = 3 6 1 4 5 2 7 8 9 10 11 12"    #it just type the new sequence,default is 123456……), but I don't know how to define other button to functions, sorry, this is all I know

---

### Post by eagle0691 on 2007-04-27
I got something more in XEV, that not a a continuous click, but a click strage. the common lmb rmb  or mmb, one click is done when you release the button, but the extra buttons is complete one click  when you just click on it . what the hell~~  what i can do then?   :confused:

---

### Post by kerry_s on 2007-04-27
[http://gentoo-wiki.com/HOWTO_Advanced_Mouse/Individual_Configurations](http://gentoo-wiki.com/HOWTO_Advanced_Mouse/Individual_Configurations)

---

### Post by eagle0691 on 2007-04-27
thank you ,but not helping, almost the same to i did

---

### Post by kerry_s on 2007-04-28
Are you restarting X when you make the changes? (ctrl+alt+backspace)

---

### Post by eagle0691 on 2007-04-28
yes, but the xmodmap could just run after X start, the problem now I see is the "ButtonPress event ButtonRelease event" is appearing in the same time ,but I still pressing the button. the other buttons will appear the ""ButtonRelease event" after I release a button. :confused:  help...

---

### Post by eagle0691 on 2007-04-28
anybody knows how? help me~

---

### Post by eagle0691 on 2007-04-30
anybody help~~

---

