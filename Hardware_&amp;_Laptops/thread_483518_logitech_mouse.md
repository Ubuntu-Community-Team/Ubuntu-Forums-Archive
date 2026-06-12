---
title: "logitech mouse"
date: 2007-06-24
forum: Hardware &amp; Laptops
---

### Post by fbs2007 on 2007-06-24
Im using an mx510...and whenever i install linux i always lose the back and forward buttons. is there anyway to change this?

any and all help is greatly appreciated

thanks

---

### Post by BobLand on 2007-06-26
Try this.  It works for my MX510 running fiesty 7.04

backup xorg.conf naming the backup with an identifier such as date, name, pets name...
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.<my_backup_name>
```

edit xorg.conf
```
sudo gedit /etc/X11/xorg.conf
```

copy this code over your existing mouse code
the red indicates code that makes this all work
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        [B][COLOR="Red"]Option          "Protocol"              "auto"
        Option          "Buttons"               "7"
        Option          "ZAxisMapping"          "4 5"
        Option          "ButtonMapping"         "1 2 3 6 7 4 5 6"[/COLOR][/B]
EndSection
```
with this mouse and fiesty, the auto protocol is recommended
the ZAxixMapping tells the wheel to emulate the up/down scroll/cruise buttons
the order of the mapping is crucial - see below

save your changes
```
ctrl-s
```
close the file
```
ctrl-q
```

restart X
```
Ctrl+Alt+Backspace
```

The screen will go black for a second or 2 then you'll see a message about running local scripts.  This may happen very quickly or it may take anywhere between a few seconds or minutes.  You will be placed back at the login screen.

That's it!  Done!
Now, test the changes

```
login
```
Open a browser window and open a few urls in the same tab.
Test all of your buttons.

The only ones that don't work (for me) are the second button from the bottom of the wheel and pressing the wheel to get smooth scrolling, but I'm working on that one.

The button mapping is as follows:
```
1 - left click
2 - middle click/scroll up/scroll down
3 - right click
4 - button above the wheel: scroll up
5 - button directly below the wheel: scroll down
6 - lower side button: go back
7 - upper side button: go forward
8 - the zen button: nothingness
```

Seems like the order of buttons in the mapping is crucial.  If you just run 1 2 3 4 5 6 7 you won't get all the buttons to work.  However, if this is a setting that is unique to particular computers then you should try different orders until you get them all to work.

If this is a dismal failure then restore your backup.  ***You did make a backup, didn't you?***
```
sudo cp /etc/X11/xorg.conf <my_backup_name> /etc/X11/xorg.conf
```

bobland

---

### Post by mikeypizano on 2007-06-26
Will this work for a VX Revolution?

---

### Post by BobLand on 2007-06-26
Mikey,
I developed this process specifically for the Logitech MX510.  What you will need to try is finding the number of buttons and what they are assigned to using xen.  If it's not installed then
```
sudo apt-get install xen
```

This program should work with any mouse.  Assuming you've got it up and running, place your pointer in the the indicated box, although it really works anywhere in that window.

Without moving the mouse begin pressing keys.  Watch the upper "main" window for **ButtonPress**.  If you move the mouse even a hair it will display the movement parameters and you'll lose the ButtonPress.  It make take a few attempts to see whats happening but just stick with it.  You'll get it.

Record the number of buttons and the sequence.  I'd guess that as long as you keep to the "red" area
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
[COLOR="Red"]        Option          "Protocol"              "auto"
        Option          "Buttons"               "7"
        Option          "ZAxisMapping"          "4 5"
        Option          "ButtonMapping"         "1 2 3 6 7 4 5 6"
[/COLOR]EndSection
```
you should be OK.  If you don't have a wheel comment out the ZAxisMapping option.  To get all the buttons working the way you want, start off with 1 thru N where N is the max number of buttons that are recognized by xen.

Run sequences beginning with 1 2 3 4 5 6 7 8 etc.... and find out which work and which don't.
For the ones that work, leave them alone.  For others, just switch around.  Example:  6 7 change to 7 6. or 4 5 8 change to 8 4 5 or 8 5 4.  You get the idea?

Hope this helps.
bobland

---

### Post by mikeypizano on 2007-06-26
I sort of get it. What about the tilt wheel? I just care about the tilt wheel, the foward and back buttons, and maybe the search buttom. I will try this though, thanks.

---

### Post by fbs2007 on 2007-06-27
just wanted to say thanks a million for your help
you made everything easy and it works wonderfully:D

---

