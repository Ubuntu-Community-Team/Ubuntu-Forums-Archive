---
title: "program to help me configure mouse buttons?"
date: 2008-07-15
forum: General Help
---

### Post by brnetonboy on 2008-07-15
i tried messing with xorg files but nothing worked and it was too complicated.

my mouse has many buttons, (including side-scroll) and i would like to take advantage of them. 

what i really need is a program that "listens" to a mouse event (which you perform by clicking or scrolling), then lets you assign what to do with that event (eg. run some program or script, change desktops, etc etc). 

does any such program exist?

---

### Post by fyo on 2008-07-16
> **brnetonboy said:**
> does any such program exist?

Yes, but you have to get Linux to recognize all your buttons first. In my experience, that doesn't happen without editing xorg.conf, but hey, I hope I'm wrong (not that it's difficult to do, see below).

To test your mouse, you could try running "xev" from a terminal and pressing your different mouse buttons inside the small square that pops up. If your mouse is correctly set up, you should see events fire in the terminal window.

I'm not sure what the best tool is for binding/mapping mouse buttons in hardy. xmodmap is not included anymore, but you might try looking here:

[http://packages.ubuntu.com/gutsy/xmodmap](http://packages.ubuntu.com/gutsy/xmodmap)
[http://packages.ubuntu.com/hardy/xbindkeys](http://packages.ubuntu.com/hardy/xbindkeys)

If your mouse is NOT set up correctly, take a look in your xorg.conf file. What does the mouse section look like? Depending on the number of buttons and so on, it should probably be something like this:

```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Buttons" "7"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "false"
    Option         "ButtonMapping" "1 2 3 6 7"
EndSection
```

---

### Post by dondad on 2008-10-30
> **brnetonboy said:**
> i tried messing with xorg files but nothing worked and it was too complicated.

my mouse has many buttons, (including side-scroll) and i would like to take advantage of them. 

what i really need is a program that "listens" to a mouse event (which you perform by clicking or scrolling), then lets you assign what to do with that event (eg. run some program or script, change desktops, etc etc). 

does any such program exist?

If you are using hardy or earlier, then get btnx and you can configure most mice. It does not work in intrepid, so you can search for evdev and xbindkeys for help there. I would post a link, but do not have access from here to my files.

---

### Post by joeoshawa on 2010-05-02
I can tell users how to rearrange there mouse button mappings if the changes are perminent or how to make them so someone else will have to tell you.

first find out what mouse you have so in a terminal $ xinput list 

here is my output

 Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=10    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® 2.4GHz Transceiver V2.0    id=8    [slave  pointer  (2)]

so the Microsoft is the one i am looking for (had to cut and paste damn trade mark) yours will be different unless you have the same or similar mouse

next $ xev

this will tell you your mouse button number click each button and write down the number

ButtonRelease event, serial 34, synthetic NO, window 0x3a00001,
root 0x1a6, subw 0x3a00002, time 9122614, (28,35), root: (699,86),
state 0×110,[COLOR=#FF0000]button 1[/COLOR],  same_screen

thank you  Messsana 

then $ xinput get-button-map " your mouse here"

my output 1 2 3 4 5 8 9 6 7 10 11 12 13 
you notice i already switched buttons 6 7 8 9 to 8 9 6 7

then $ xinput set-button-map "your mouse here" 1 2 3 4 5 6 7 8 9
stop after the buttons you wish to change
DO NOT LEAVE OUT SPACES! or have fun with your messed up mouse

that's it

now if i could only add new buttons i want to have a copy paste functioning and i have unassigned buttons

---

### Post by dargaud on 2010-11-16
joeoshawa, your solution works for removing or reordering buttons, but how do you actually _do_ something with all those extra buttons ? For instance assign PageUp to button 10 and the like. There are plenty of old posts mentioning the btnx utility, but they also end by stating that btnx doesn't work in recent Ubuntus. And indeed it doesn't. So what's the solution ?

---

### Post by rare HERO on 2011-07-24
> **joeoshawa said:**
> 
...

my output 1 2 3 4 5 8 9 6 7 10 11 12 13 
you notice i already switched buttons 6 7 8 9 to 8 9 6 7

then $ xinput set-button-map "your mouse here" 1 2 3 4 5 6 7 8 9
stop after the buttons you wish to change
DO NOT LEAVE OUT SPACES! or have fun with your messed up mouse
...



What do the numbers mean?

---

