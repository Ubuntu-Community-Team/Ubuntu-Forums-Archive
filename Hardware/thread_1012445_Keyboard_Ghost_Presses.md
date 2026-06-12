---
title: "Keyboard Ghost Presses"
date: 2008-12-15
forum: Hardware
---

### Post by Nemesis02 on 2008-12-15
Hi everybody, i'm having a problem with my HP Pavilion DV5000z laptop.  Basically, i'll be typing and stuff like my browser will go back 1 page or my desktop will change from 1 to 2.  Just key presses happen at random.  I'll be talking in pidgin and the IMer window changes or the window menu comes up.

Has anyone had this problem before? If so, how do i fix this? It's quite annoying...

I have the new Ubuntu 8.10 Intrepid and i'm all up to date.

---

### Post by hardyn on 2008-12-15
are you maybe brushing the touchpad with your wrist and "tapping" the keypad?  I have done that before, it is also very easy to disable tapping.

if you like tapping there is some xorg.conf work that will disable the mouse when you are typing, it is on the forum somewhere.

you could possibly have defective keyboard / touchpad as well, that is a little more money to fix and a little harder to diagnose if it is intermittent.

good luck.

---

### Post by cdtech on 2008-12-15
I had a problem with my HP. I selected the "System > Preferences > Keyboard" then the "layout" tab and chose the "Evdev-managed keyboard". Now it works like it should. I could press the up arrow and it woud take a screenshot. lol

Hope this helps.....

---

### Post by Nemesis02 on 2008-12-15
> **hardyn said:**
> are you maybe brushing the touchpad with your wrist and "tapping" the keypad?  I have done that before, it is also very easy to disable tapping.

if you like tapping there is some xorg.conf work that will disable the mouse when you are typing, it is on the forum somewhere.

you could possibly have defective keyboard / touchpad as well, that is a little more money to fix and a little harder to diagnose if it is intermittent.

good luck.

I'm fairly sure i'm not hitting the touchpad, i type like approx. 80 words per minute.  It only happens while i type, and while i'm typing i'm not tapping my mouse.

---

### Post by Nemesis02 on 2008-12-15
> **cdtech said:**
> I had a problem with my HP. I selected the "System > Preferences > Keyboard" then the "layout" tab and chose the "Evdev-managed keyboard". Now it works like it should. I could press the up arrow and it woud take a screenshot. lol

Hope this helps.....

Where's evdev-managed keyboard under layout? I see keyboard layout set to Generic 105 key (intl) PC and Selected Layout set to USA and seperate layout for each window is set.

---

### Post by Nemesis02 on 2008-12-15
> **Nemesis02 said:**
> Where's evdev-managed keyboard under layout? I see keyboard layout set to Generic 105 key (intl) PC and Selected Layout set to USA and seperate layout for each window is set.

Nvm, found it, its under keyboard model.

---

### Post by Nemesis02 on 2008-12-15
I tried changing the keyboard model like the previous post said and it didn't work.  I'll be typing and it'll either change the position of my cursor, or back the page up or do somethin crazy like that.

---

### Post by Nemesis02 on 2008-12-17
I'm still having the random button press issue with my laptop.  I'll be typing a rather lengthy post, and the page will go back one, or i'll be typing and the line changes.  I use the touchpad, but i don't use the tap to click option, so if its that, how would i go around to disabling it?

---

### Post by Ng Oon-Ee on 2008-12-17
There should be some key-combo on your laptop for disabling the touchpad. Otherwise, search these forums for guides on the matter, search the word SHMConfig, it'll most likely turn  up as the first few results.

---

### Post by Nemesis02 on 2008-12-17
> **Ng Oon-Ee said:**
> There should be some key-combo on your laptop for disabling the touchpad. Otherwise, search these forums for guides on the matter, search the word SHMConfig, it'll most likely turn  up as the first few results.

K, well, i found bout howto disable it, but my problem now is i don't have the section for the input device touchpad in my xorg.conf file.  There's no input device for the mouse on there at all...

---

### Post by Ng Oon-Ee on 2008-12-17
Add one. For reference, here's the important parts from my own xorg.conf....

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Synaptics Touchpad" "CorePointer"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "CorePointer"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
    Option         "SHMConfig" "on"
EndSection
```

You could probably just use that whole section on InputDevice. Remember to add a refernce to it in the ServerLayout.

---

### Post by Nemesis02 on 2008-12-20
> **Ng Oon-Ee said:**
> Add one. For reference, here's the important parts from my own xorg.conf....

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Synaptics Touchpad" "CorePointer"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "CorePointer"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
    Option         "SHMConfig" "on"
EndSection
```

You could probably just use that whole section on InputDevice. Remember to add a refernce to it in the ServerLayout.

Thanks, i believe this solved the problem I was having.  I added that to my /etc/X11/xorg.conf file and matched it to look like yours and haven't had a problem with my keyboard since.

Appreciate it.

---

