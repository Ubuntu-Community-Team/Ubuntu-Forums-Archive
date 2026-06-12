---
title: "Toshiba Satellite R10 - How to get Tablet to rotate or buttons to work?"
date: 2011-01-22
forum: Hardware
---

### Post by jfaurbo on 2011-01-22
Hi,

I'm a brand new user to Linux. I have a Toshiba Satellite R10 tablet (PSR10C-AN503E).

I installed the newest version 10.10 and the Pen Worked automatically. However the toshiba tablet buttons don't work and when i rotate my tablet the screen orientation won't change. 

I have tried to find something on the forum but everything that i read has to do with older versions (i think) and i'm not sure what to do. 

Can someone walk me through what to do, Please.

Thanks

---

### Post by Favux on 2011-01-22
Hi jfaurbo,

Welcome to Ubuntu forums!

You should be able to use a rotation script from the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").  Methods 1 or 3 should work for you.  And as described running xev you can press your bezel buttons and see if they're giving a keycode we could use.

Or if you like we could take a quick look putting Toshiba's into Magick Rotation (method 4).

Either way we want to look at the output in a terminal of:
```
xinput list
```
And if you're interested in Magick also post the output of:
```
sudo lsinput
```
And this will also help us look at your bezel buttons.  To do the lsinput you may require install of input-utils:
```
sudo apt-get install input-utils
```

---

### Post by jfaurbo on 2011-01-23
Here is the xinput list:

```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                                  id=10    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=11    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser                  id=12    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus                  id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=9    [slave  keyboard (3)]
    &#8627; Toshiba input device  
```Here is the response to lsinput

```
/dev/input/event0
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x5
   version : 0
   name    : "Lid Switch"
   phys    : "PNP0C0D/button/input0"
   bits ev : EV_SYN EV_SW

/dev/input/event1
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x1
   version : 0
   name    : "Power Button"
   phys    : "PNP0C0C/button/input0"
   bits ev : EV_SYN EV_KEY

/dev/input/event2
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x1
   version : 0
   name    : "Power Button"
   phys    : "LNXPWRBN/button/input0"
   bits ev : EV_SYN EV_KEY

/dev/input/event3
   bustype : BUS_I8042
   vendor  : 0x1
   product : 0x1
   version : 43841
   name    : "AT Translated Set 2 keyboard"
   phys    : "isa0060/serio0/input0"
   bits ev : EV_SYN EV_KEY EV_MSC EV_LED EV_REP

/dev/input/event4
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x6
   version : 0
   name    : "Video Bus"
   phys    : "LNXVIDEO/video/input0"
   bits ev : EV_SYN EV_KEY

/dev/input/event5
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "Toshiba input device"
   phys    : "\_SB_.VALZ"
   bits ev : EV_SYN EV_KEY

/dev/input/event6
   bustype : BUS_I8042
   vendor  : 0x2
   product : 0x8
   version : 0
   name    : "PS/2 Mouse"
   phys    : "isa0060/serio1/input1"
   bits ev : EV_SYN EV_KEY EV_REL

/dev/input/event7
   bustype : BUS_I8042
   vendor  : 0x2
   product : 0x8
   version : 29473
   name    : "AlpsPS/2 ALPS GlidePoint"
   phys    : "isa0060/serio1/input0"
   bits ev : EV_SYN EV_KEY EV_ABS

```

I tried looking at the How-to for tablets and i get lost. I'm sorry that in this case i'm rather technically inexperienced.

---

### Post by Favux on 2011-01-23
Hi jfaurbo,

Unfortunately nothing jumps out at me that we could use in Magick.  We'd want to see something else with:
```
bits ev : EV_SYN EV_SW

```
other than the "Lid Switch".  Since that's probably to put your tablet to sleep or whatever.  We'd want to see a EV_SW (event switch) somewhere else.  Oh well.

So does your tablet pc have stylus and eraser and no touch?  If so for you a method 1 script would look like:
```
#!/bin/sh 

# Find the line in "xrandr -q --verbose" output that contains current screen orientation and "strip" out current orientation. 

rotation="$(xrandr -q --verbose | grep 'connected' | egrep -o  '\) (normal|left|inverted|right) \(' | egrep -o '(normal|left|inverted|right)')" 

# Using current screen orientation proceed to rotate screen and input tools. 

case "$rotation" in 
    normal) 
#    -rotate to the right 
    xrandr -o right 
    xsetwacom set "Serial Wacom Tablet stylus" CW 
    xsetwacom set "Serial Wacom Tablet eraser" rotate CW  
    ;; 
    right) 
#    -rotate to normal 
    xrandr -o normal 
    xsetwacom set "Serial Wacom Tablet stylus" rotate NONE 
    xsetwacom set "Serial Wacom Tablet eraser" rotate NONE 
    ;; 
esac
```
Then follow the instructions in "Now with the preliminaries out of the way let's get down to rotating".

---

### Post by jfaurbo on 2011-01-23
I'm sorry... i don't know how to input that into the approriate executable...

I know that i'm suppose to select the bin/sh file... but i can't get past my intial prompt:

```
john@john-Satellite-R10:~$
```

the directory of which only looks like:

```
john@john-Satellite-R10:~$ dir
Desktop    Downloads         Java   Pictures  Templates
Documents  examples.desktop  Music  Public    Videos
```

so, now that I've embarrassed myself... please tell me how i get to my systems root directory.

---

### Post by Favux on 2011-01-23
Right click on your Desktop and chose create Document > empty file.  Then call it .rotate.sh.  Using the . in front will make it a hidden file so to find it again check View hidden files in Places (Nautilus).  Open it in the text editor gedit (gnome text editor) and copy and paste the script into it and save.  Then right click on it and in the Permissions tab check the "Allow executing file as a program" check box.  Then right click on the Desktop and create Launcher.  Then in the launcher put the path to your new executable rotation file:
```
/home/yourusername/Desktop/.rotate.sh
```
Now double clicking on the launcher should cause rotation.  You can move .rotate.sh to youryousername directory later (drag it there).  Remember to change the path in the laucher if you do:
```
/home/yourusername/.rotate.sh
```
You can also drag the launcher into a panel and then a single click will run the rotation script.

---

### Post by jfaurbo on 2011-02-14
Thanks for the detailed explanation... However it doesn't seem to work.

I think it might have something to do with my monitor. I don't believe that I have any drivers for it. This is based on the fact that the screen seems very dim, and I'm not able to use any of the visual enhancements. There are a few other things too, can't play video and graphics programs seem to have difficulty rendering.

Maybe I'm just expecting to much from my old machine.

Let me know what the next step is. 

Thanks

---

