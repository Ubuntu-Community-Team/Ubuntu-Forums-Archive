---
title: "Drawing Tablet - Stylus Button remap"
date: 2017-03-03
forum: Hardware
---

### Post by pproets on 2017-03-03
Hi folks,
I bought myself a XP-PEN Star03 drawing tablet and on linux everything works fine, both pressure detection in Krita and also the buttons seem to be recognised.
However, Button 2 and 3 are defined as "drag the canvas around" and "pick a color". I want to overwrite the function of Button 2 (drag canvas around) and I want to put in the keystrokes Crtl_L + z for "undo" command. 
However remapping this button eats me up. 
xinput told me that there are 3 virtual core pointers named 'UC-Logic TABLET 1060N' , but different amounts of mousebuttons:
```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; USB Laser Game Mouse                        id=8    [slave  pointer  (2)]
&#9116;   &#8627; USB Laser Game Mouse                        id=10    [slave  pointer  (2)]
&#9116;   &#8627; UC-Logic TABLET 1060N                       id=13    [slave  pointer  (2)]
&#9116;   &#8627; UC-Logic TABLET 1060N                       id=14    [slave  pointer  (2)]
&#9116;   &#8627; UC-Logic TABLET 1060N                       id=15    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; USB Laser Game Mouse                        id=9    [slave  keyboard (3)]
    &#8627; Logitech Gaming Keyboard G105               id=11    [slave  keyboard (3)]
    &#8627; Logitech Gaming Keyboard G105 

```
```
xinput get-button-map 13
1 2 3 4 5 

```
```
xinput get-button-map 14
1 2 3 4 5 6 7 8 9 10 11 12 13

```
```
xinput get-button-map 15
1 2 3 4 5 6 7

```

the tablet itself has 8 buttons, the pen has the tip, and 2 additional buttons. I assume that the tip is recognised as left mouse-button click, the second button as middle-mouse button click and the last as right mouse button click
since there should be a theoretical possibility to turn the "mousewheel" (i.e. the second button in the pen - recognized as middle mouse button = mousewheel) the ID 13 should be my pen. maybe.

Now I want my system (via xte) to produce a Control_L + Z when I click this button on the pen. 
I verified that the button I want to remap is indeed Button 2 (via xev)
Now I created a xbindkeys cfg file in my home dir and started xbindkeys
```
xbindkeys -defaults > ~/.xbindkeysrc
```
and wrote the default rc file into the new xbindkeysrc in my home directory

now in combination with xte and xbindkeys I wanted to reconfigure my pen button. in the .xbindkeysrc file I added:

```
"xte -i 13 'keydown Control_L' 'key z' 'keyup Control_L'" b:2
```
now the problem with this is, that ID 13 is recognized as a mouse and therefore cannot produce keyboard keystrokes. so -i 13 is wrong. I would have to choose either id 9 or 11 for these are recognized as my logitech keyboard. however, this line: 
```
"xte -i 9 'keydown Control_L' 'key z' 'keyup Control_L'" b:2 
``` doesn't work and if it would work, it would overwrite my middle mouse button of my regular mouse.
But I only want my pen-button to be reconfigured. 
Also why does it not work? Do I need a reboot or something? Or is it not possible to put crtl + z on one mouse click? 

Any ideas what I could try else?

Thanks a lot

---

### Post by Irihapeti on 2017-03-03
*Thread moved to **Hardware**.*

---

### Post by pdc on 2017-03-04
so in post #5 [https://ubuntuforums.org/showthread.php?t=2326961](https://ubuntuforums.org/showthread.php?t=2326961)

a user from Manjaro talked about the wrong mapping of buttons

is there anything of use to you here?

---

### Post by pproets on 2017-03-04
Thanks for the reply !
I'm not sure if I want to install different drivers since the device get's detected and works. the only thing I want to do is to remap. And I can see where the problem is: with xte I can choose the device that is used for the output (ctrl + z from the keyboard - id = 9 or 11) with the -i parameter, but I cannot choose the input device, which would be my tablet pen. if there is a program in which I can choose both devices, then the problem should be fixed imo. But I guess I'll give it a try in a few hours. Is there a way to uninstall the drivers again in case they create some kind of conflict?

Update: it seems to work now, I guess I just needed to reboot O_o
however, since the mouse-wheel click and the button 2 or my stylus pen seem to be recognized as the same mousebutton, I can't use my mouse-wheel click anymore, since it produces ctrl + z with each click. 
do you know a program, that can map keys to a specific device ?

---

### Post by pdc on 2017-03-04
"do you know a program, that can map keys to a specific device ? "

No; I would look to a specialist forum; whether there is a wacom forum even as that is likely the longest running group .....

eg 

[http://forum.wacom.eu/viewforum.php?f=4&sid=0558960258decc496e7c7492616569ce](http://forum.wacom.eu/viewforum.php?f=4&sid=0558960258decc496e7c7492616569ce)

or you could try [https://sourceforge.net/projects/linuxwacom/](https://sourceforge.net/projects/linuxwacom/) for pointers: some very knowledgable folks there

---

### Post by pproets on 2017-03-07
thanks for the reference !

---

