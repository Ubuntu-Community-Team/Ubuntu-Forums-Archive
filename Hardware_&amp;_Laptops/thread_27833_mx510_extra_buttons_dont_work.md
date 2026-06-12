---
title: "mx510 extra buttons dont work"
date: 2005-04-17
forum: Hardware &amp; Laptops
---

### Post by jnev on 2005-04-17
i'm running kubuntu hoary 5.04 and the side buttons of my mx510 don't work at all. they're supposed to allow me to go forward and backward while browsing. when i used mepis i just had to go into the xf86config-4 file and change the number of buttons from 5 to 8. i'm not sure how this is dont in xorg.conf however. 

thanks

---

### Post by jnev on 2005-04-17
also, my sound doesn't work at all. i have onboard sound. the motherboard is an abit aa8xe

---

### Post by jnev on 2005-04-18
bump

---

### Post by jnev on 2005-04-18
can anyone help me??

---

### Post by fipeso on 2005-04-19
Hi,

Using this link:

[http://gentoo-wiki.com/HOWTO_Mouse_Nav_Buttons](http://gentoo-wiki.com/HOWTO_Mouse_Nav_Buttons)

I got the thumb buttons to work on my Ubuntu last night.
(I have a MX500 though)

---

### Post by jnev on 2005-04-19
i did what they said, now all the functions of the buttons are screwed up. when i try to scroll down the browser goes 'back'. a side button does the same thing as right-click. how do i set the functions of each button??

---

### Post by Dinler on 2005-04-19
[QUOTE=jnev]i did what they said, now all the functions of the buttons are screwed up. when i try to scroll down the browser goes 'back'. a side button does the same thing as right-click. how do i set the functions of each button??[/QUOTE]

I have MX700 and: 

1. (sudo) gedit /etc/X11/XF86Config-4 (xorg.conf)

2. Edit the mouse section to:
Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "4 5"
Option "Buttons" "9"
EndSection

3. Install imwheel (I think that you can: sudo apt-get install imwheel)

4. (sudo) gedit /etc/X11/imwheel/imwheelrc

5. Remove everything in the document and add:
#Firefox Settings
"^.*firefox$"
None, Left, Alt_L|Left
None, Right, Alt_L|Right
Control_L, Left, Control_L|Left
Control_L, Right, Control_L|Right

#Default Settings
".*"
@Priority = -1000
None, Left, Control_L|Left
None, Right, Control_L|Right
Control_L, Left, Control_L|Left
Control_L, Right, Control_L|Right 

Change "firefox" to your browser!

6. sudo cp /etc/X11/imwheel/imwheelrc ~/imwheelrc

7. Restart X (CTRL + ALT + BACKSTAGE)

8. FINISH!

---

### Post by jnev on 2005-04-19
THANK YOU!!! that worked perfectly...


does anyone know how to get my sound working? details are in my 1st post...

---

