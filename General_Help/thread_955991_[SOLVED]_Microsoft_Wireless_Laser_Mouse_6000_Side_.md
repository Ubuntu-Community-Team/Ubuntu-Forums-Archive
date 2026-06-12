---
title: "[SOLVED] Microsoft Wireless Laser Mouse 6000 Side Buttons Not Workign"
date: 2008-10-22
forum: General Help
---

### Post by blis102 on 2008-10-22
Hell everyone,

I am running Ubuntu 8.04 and am having difficulty with my Microsoft Wireless Laser Mouse 6000 two side buttons. They are behaving like buttons 2 and 3. 

When I run "xev" and click the side buttons I get:

```
ButtonPress event, serial 30, synthetic NO, window 0x2600001,
    root 0x253, subw 0x0, time 326444, (175,172), root:(180,227),
    state 0x10, button 3, same_screen YES

ButtonRelease event, serial 30, synthetic NO, window 0x2600001,
    root 0x253, subw 0x0, time 326623, (175,172), root:(180,227),
    state 0x410, button 3, same_screen YES

ButtonPress event, serial 30, synthetic NO, window 0x2600001,
    root 0x253, subw 0x0, time 327799, (175,172), root:(180,227),
    state 0x10, button 2, same_screen YES

ButtonRelease event, serial 30, synthetic NO, window 0x2600001,
    root 0x253, subw 0x0, time 327935, (175,172), root:(180,227),
    state 0x210, button 2, same_screen YES
```

My /etc/X11/xorg.conf file looks like:

```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection
```

I have tried to change this around a bit with no luck.

Does anyone successfully have a Microsoft Wirelss Laser Mouse 6000 working with Ubuntu 8.04? If so, what is your xorg.conf entry look like? Any ideas about how I can get the side buttons to work right (forward/back history)

---

### Post by dcstar on 2008-10-23
> **blis102 said:**
> Hell everyone,

I am running Ubuntu 8.04 and am having difficulty with my Microsoft Wireless Laser Mouse 6000 two side buttons. They are behaving like buttons 2 and 3. 
.........
Does anyone successfully have a Microsoft Wirelss Laser Mouse 6000 working with Ubuntu 8.04? If so, what is your xorg.conf entry look like? Any ideas about how I can get the side buttons to work right (forward/back history)

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/52288](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/52288)

---

### Post by blis102 on 2008-10-26
Thanks dcstart but I tried what they recommended and it didn't fix the problem.

Some xorg.conf changes Ive tried:

```
Section "InputDevice"
    Identifier "Configured Mouse"
    Driver "mouse"
    Option "CorePointer"
    Option "Device" "/dev/input/mice"
    Option "Protocol" "ExplorerPS/2"
    Option "ZAxisMapping" "4 5"
    Option "Emulate3Buttons" "true"
    Option "Buttons" "7"
    Option "ButtonMapping" "1 2 3 6 7"
EndSection
```

```
Section "InputDevice"
    Identifier "Configured Mouse"
    Driver "mouse"
    Option "CorePointer"
    Option "Device" "/dev/input/mice"
    Option "Protocol" "auto"
    Option "ZAxisMapping" "4 5"
    Option "Emulate3Buttons" "true"
    Option "Buttons" "7"
    Option "ButtonMapping" "1 2 3 6 7"
EndSection
```

```
Section "InputDevice"
    Identifier "Configured Mouse"
    Driver "mouse"
    Option "CorePointer"
    Option "Device" "/dev/input/mice"
    Option "Protocol" "auto"
    Option "ZAxisMapping" "4 5"
    Option "Emulate3Buttons" "true"
    Option "ButtonMapping" "1 2 3 7 6"
EndSection
```

Does anyone have a working Microsoft Wireless Laser Mouse 6000?

Thanks~!

---

### Post by blis102 on 2008-10-26
BTW, this is the mouse that I am speaking of:

[http://content.etilize.com/images/300/10520957.jpg](http://content.etilize.com/images/300/10520957.jpg)

It seems like there are a lot of Microsoft Wireless Laser 6000s out there...

Hope that helps

---

### Post by blis102 on 2008-10-26
Oh and the model number is 1052

---

### Post by CatKiller on 2008-10-26
Don't forget to restart X (Ctrl-Alt-Backspace) for the changes to xorg.conf to take effect.

Also, Back and Forward don't work with the side buttons by default in Nautilus (the file manager) - I believe that you need to install a script to get that behaviour in Nautilus.

Another thing; I seem to recall that Firefox has the buttons doing something else by default, too. If you go to **about:config** in Firefox and look for the **mousewheel.horizscroll.withnokey keys**. **.action** should be **2**, **.numlines** should be **-1**, and **.sysnumlines** should be **false**.

I can't offer you more specific help with your mouse, since I'm quite happy with my Logitech G3, but I hope the information has been helpful.

---

### Post by blis102 on 2008-10-26
I got the back/forward buttons to work in Firefox!

All I did was follow this tutorial and restart X:

[http://ubuntuforums.org/showpost.php?p=103285&postcount=57](http://ubuntuforums.org/showpost.php?p=103285&postcount=57)

Now all I need to figure out is how to get Nautilus back/forward to work...

Thanks!

---

