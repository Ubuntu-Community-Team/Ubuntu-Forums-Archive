---
title: "mouse is frozen!     help!!!"
date: 2005-11-29
forum: General Help
---

### Post by nacho32 on 2005-11-29
I have a non usb mouse 2 buttons 1 wheel optical mouse
maker GE . I can log in but thats it mouse is frozen.
please help this newbie.

---

### Post by Morphius on 2005-11-29
You may need to check your /etc/X11/xorg.conf file. Please post the section titled "InputDevice" with the identifier "Generic Mouse"

---

### Post by nacho32 on 2005-11-29
[QUOTE=Morphius]You may need to check your /etc/X11/xorg.conf file. Please post the section titled "InputDevice" with the identifier "Generic Mouse"[/QUOTE]
how do I do that Im total newb with this i have dual boot xp on computer

---

### Post by tukuyomi on 2005-11-29
Browse with nautilus to find **/etc/X11/xorg.conf** then open it with a text editor (gedit, ...) (Alternatively, open a Terminal (Application -> Accessories) and write ```
gedit /etc/X11/xorg.conf
*X11 <-- with uppercase X*

```
Then find the section ```
Section "InputDevice"
        Identifier      "Configured Mouse" *(or "Generic Mouse")*
```, copy it (until the End Section) and paste it in this forum!

---

### Post by nacho32 on 2005-11-29
[QUOTE=tukuyomi]Browse with nautilus to find **/etc/X11/xorg.conf** then open it with a text editor (gedit, ...) (Alternatively, open a Terminal (Application -> Accessories) and write ```
gedit /etc/X11/xorg.conf
*X11 <-- with uppercase X*

```
Then find the section ```
Section "InputDevice"
        Identifier      "Configured Mouse" *(or "Generic Mouse")*
```, copy it (until the End Section) and paste it in this forum![/QUOTE]
Im total lost Ican log in and thats it no mouse movement , durring the boot the mouse light goes off when the OS is loading:(

---

### Post by tukuyomi on 2005-11-29
Try this:
Press ALT and F2 at the same time and type the command ```
gedit /etc/X11/xorg.conf
```
then with your keyboard arrows, scroll down to the file until you reach the section to copy/paste.
Select the section with SHIFT and arrows, copy the selection with CTRL + C then paste with CTRL + V.

---

### Post by Morphius on 2005-11-29
Because you cannot use your mouse in gnome, you can't really use gedit. Therefore you should use vim. As such, you will need to do the following:

ctl+alt+f1 to enter a tty terminal. This is the command line backed of linux.

log in

enter the following command "sudo vim /etc/X11/xorg.conf" The commad is case sensitive so not the uppercase x in the path

write down and post *exactly* what is says in the section "inputdevice" which has the identifier "generic mouse"

notes:
you use the up/down arrows to navigate the xorg file.

you will need to input your *root* password that you specified during the ubuntu installation after the "sudo ..." command

use ctl+alt+f7 to return to the gnome terminal.

---

### Post by nacho32 on 2005-11-29
here is what it says
selection"inputdevice"
Identifier     "configured mouse"
Driver          'mouse"
OPTION        "corePointer"
Option          "device"               "/dev/input/

mice'
    option      "protocol"      "I mPS/2
     option      "Emulate3buttons         "true"
    option        "ZAXisMapping"            "4.5"

i had to type this out on a lap top
it,s a non usb mouse optical 2 buttons and wheel in middel brand GE

---

### Post by nacho32 on 2005-11-29
[QUOTE=nacho32]here is what it says
selection"inputdevice"
Identifier     "configured mouse"
Driver          'mouse"
OPTION        "corePointer"
Option          "device"               "/dev/input/

mice'
    option      "protocol"      "I mPS/2
     option      "Emulate3buttons         "true"
    option        "ZAXisMapping"            "4.5"

i had to type this out on a lap top
it,s a non usb mouse optical 2 buttons and wheel in middel brand GE[/QUOTE]

odd thing to is I have dual boot and the mouse is still frozen when I go back to XP, I have to unplug it and plug it back in for xp , then I have to restart then it works fine in xp but as soon as I go into ubuntu it just seems froze and messes up xp mouse functions aswell

---

### Post by Morphius on 2005-11-29
OK, I would try this:

Change the line:

option "protocol" "ImPS/2"
to
option "protocol" "PS/2"

This will remove scroll wheel functionality, but we can change it back later. We're just simplifying things to eliminate problems. If you want the scroll wheel change it back after we have fixed the problem.

Also change:

Option	"Device"  		"/dev/input/mice"
to
Option	"Device"  		"/dev/psaux"

To edit using vim:

Follow the instructions from before and then:
press "i" or insert to be able to write using vim, make your changes and then press escape and type ":wq" and press return. (w is for write, q is for quit)

You will need to re-boot the computer after making these changes, therefore, after returning to the command prompt, type "reboot"

PS
You did check the connection and tried another mouse? No offense, just double checking the easy stuff.

---

### Post by nacho32 on 2005-11-29
thxs for the reply, I had to use temanal like the other guysaid when i tryed yourway after i log on it asked for a password?
I think Im gona wait till they make this os more user friendly, seems like Im spending tomuch time on it just to get a mouse to work, shame looked like a nice OS
thxs for your time

---

