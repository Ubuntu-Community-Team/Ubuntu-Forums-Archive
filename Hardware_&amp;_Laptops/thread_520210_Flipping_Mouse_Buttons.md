---
title: "Flipping Mouse Buttons"
date: 2007-08-07
forum: Hardware &amp; Laptops
---

### Post by fppl on 2007-08-07
**This post could be related to an Ubuntu bug filed at**: [http://img241.imageshack.us/img241/8611/screenshotrootyamdesktoxl1.png](http://img241.imageshack.us/img241/8611/screenshotrootyamdesktoxl1.png) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi,
I couldn't find any thread about this.

Just today I decided to move to Linux, and I picked Ubuntu 7.0.4.

I wanted to activate my thumb buttons for my Microsoft Laser Mouse 6000 and after following a lot of tutorials and threads and guides for several hours, I finally managed to do it.

Now I only have one problem: The buttons work and do what they should... Kind of. :P The button that's supposed to go Back is going Forward and vice versa.

I went into imwheel help and saw that there was a way to flip their actions permanently by getting into Konsole and typing imwheel --flip-buttons -b"67", but when I do that it gives me tons of error messages saying "Unrecognized wheel action in config. Ignored action." and so it does, ignores it, and nothing happens. :(

If you can tell me how to switch my buttons' actions I'd greatly appreciate it. Thanks. :)

---

### Post by fppl on 2007-08-08
Anyone?

---

### Post by fppl on 2007-08-08
Please help me with this I've been sitting here for like 10 hours trying to figure this out...

Ok, I figured I hadn't told imwheel to start up with my X session, now it does. Also, I figured I have 2 scrolling axes so I did imwheel -k -b "0 0 0 0 6 7" and got no errors... But the buttons still do the same thing. I still need to switch them!

Please, I know SOMEONE here must know how to do such a thing.

---

### Post by fppl on 2007-08-08
By the way,
Button 6 (I did the imwheel -c to figure this out) is the forward button, and 7 is the back button.

Here's my imwheelrc config for firefox

"^Firefox-bin$"
None,Button7,Alt_L|Left
None,Button6,Alt_L|Right

And my xconf mouse config:

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
Option "Buttons" "7"
Option "ButtonMapping" "1 2 3 7 6"
EndSection

---

### Post by fppl on 2007-08-08
Can anyone help me here please?

---

### Post by fppl on 2007-08-08
Is my thread invisible..?

---

### Post by fppl on 2007-08-09
still waiting..

---

### Post by fppl on 2007-08-10
Ok it's kinda sad that no one reached out to help me solve this simple manner, but after many trials I found a solution (so if anyone finds this thread and needs a solution for this problem here goes)

I just edited my xconf mouse config to this

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
Option "Buttons" "7"
Option "ButtonMapping" "1 2 3 7 6"
EndSection

Key line: button mapping 7 and then 6 instead of 6 and then 7.

---

