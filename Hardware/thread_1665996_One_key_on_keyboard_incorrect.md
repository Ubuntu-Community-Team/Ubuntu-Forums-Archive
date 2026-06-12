---
title: "One key on keyboard incorrect"
date: 2011-01-13
forum: Hardware
---

### Post by janthonywj on 2011-01-13
After a lot of searching I haven't been able to track down a solution to this problem. I'm not familiar with the keyboard mapping settings. 

I installed Kubuntu 10.10 for my brother on his Asus G60V gaming laptop, and he's picking it up nicely. However, he noticed that the backslash key (right below backspace) is incorrect. It gives you < and with shift added it gives > instead of the vertical bar it should. All other keys seem to be correct and the function keys work properly OOB. 

In the keyboard settings, the keyboard model is set to Asus [vertical bar I can't type] Asus Laptop. Everything seems set right. Manually change the key output somehow? Somehow verify the correct signal is being sent from the hardware?

I appreciate anyone that can help me.

---

### Post by Zorael on 2011-01-13
Yes, you can rebind pretty much all keys, except hardware-bound or bios-governed stuff like Fn. I don't know what the KDE keyboard layout manager does, but the environment-independent way is to use **xmodmap**.

Open up a terminal and run '**xev**'. Focus the little white window that pops up and hit your key. Note what **keycode** is listed in the terminal output. Then Ctrl+C to exit.

Example output;
```
***[...]***
KeyPress event, serial 34, synthetic NO, window 0x1a00001,
    root 0xaa, subw 0x0, time 314970136, (690,-128), root:(692,257),
    state 0x0, **keycode 61** (keysym 0x2d, minus), same_screen YES,
    XLookupString gives 1 bytes: (2d) "-"
    XmbLookupString gives 1 bytes: (2d) "-"
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x1a00001,
    root 0xaa, subw 0x0, time 314970205, (690,-128), root:(692,257),
    state 0x0, **keycode 61** (keysym 0x2d, minus), same_screen YES,
    XLookupString gives 1 bytes: (2d) "-"
    XFilterEvent returns: False
***[...]***
```
All right, so as an example, my minus key has the keycode **61**. The command '**xmodmap -pke**' will list all current keycodes and what they are bound to, but here we're only interested in 61. (Obviously, replace that with what your output shows.)
```
$ xmodmap -pke | grep 61
keycode  **61** = minus underscore minus underscore dead_belowdot dead_abovedot
keycode **161** =
```
As we **grep** the output for **61**, it will also obviously catch 1**61**, but just ignore that one. If you can't enter the pipe or bar character (**|**, which I imagine is the one you mean by vertical bar), just skip the grep part and scroll up to find your keycode.

Anyway, those words after the equality sign are **symbols**. The first one is the symbol that gets sent if you press the key normally (minus), the second one if pressed with shift (underscore). I think you have to enable extra modifiers for the third and fourth symbol. The fifth and sixth are when pressed with AltGr (dead_belowdot) and Shift+AltGr (dead_abovedot) respectively.

Many symbols are self-explanatory (a A b B minus plus quote backslash, etc), but for a list of more obscure ones, install the **x11proto-core-dev** package, then open up **/usr/include/X11/keysymdef.h** in a text editor.

So, let's try modifying it. Just assume keycode 61 is your slash/pipe key. I use a Swedish keyboard myself and I don't know what your keyboard layout is like, so I'm just guessing now.
```
$ xmodmap -e 'keycode 61 = backslash bar'
```
The changes should be immediate. If nothing happened, doublecheck that you have the right keycode. Try again with different symbols, or add more as you please. Remember that the third and fourth symbols likely need you to enable an extra modifier (beyond Shift, Alt, Control and AltGr), and the fifth and sixth need you to have an AltGr key. You can create a custom one, but I don't know the details on how to do that.

If you find a combination that works, save it to a script that gets run when you login. Such as **~/.kde/Autostart/fixkeys**;
```
#!/bin/bash
xmodmap -e 'keycode 61 = backslash bar'
```
Remember to set it as executable.

In the KDE version that's in the main maverick repositories (4.5.1), you can save the part inbetween the quotes to **~/.Xmodmap**, and upon logging in it will automatically run the xmodmap command on it and execute its contents.
```
keycode 61 = **backslash bar**
```
This functionality is broken in 4.5.85 and onwards, for which there's a bug entry [over on Launchpad](https://bugs.launchpad.net/kubuntu-ppa/+bug/688515). You can circumvent it by creating the startup script instead as above, or by creating another script that just executes the .Xmodmap file (which is the preferred behavior).
```
#!/bin/bash
xmodmap ~/.Xmodmap
```

Lastly, a real-life example. I rebound my Caps Lock key, since I never ever ever use it except when I hit it accidentally. It's now **F35** when hit normally, and normal Caps Lock if hit with Shift, just incase I still need it. Then I bound Yakuake to roll down when I hit F35. I picked such a high number just to avoid collisions. So my **~/.Xmodmap**;
```
keycode 66 = F35 Caps_Lock
```

---

### Post by janthonywj on 2011-01-13
Thank you Zorael. Your explanation was very helpful and thorough. Good work and thanks again. Worked like a charm. 

This is one of the reasons I love the Linux community.

---

### Post by uauaua on 2011-06-24
i want to remap my tab to cap locks then vice versa..but when i change the cap locks it turn to be tab and also cap locks.then the tab have no function..how i can change successfully???

help!!

---

### Post by tacklestar on 2011-06-24
> **Zorael said:**
> Yes, you can rebind pretty much all keys, except hardware-bound or bios-governed stuff like Fn. I don't know what the KDE keyboard layout manager does, but the environment-independent way is to use **xmodmap**.
 
Open up a terminal and run '**xev**'. Focus the little white window that pops up and hit your key. Note what **keycode** is listed in the terminal output. Then Ctrl+C to exit.
 
Example output;
```
***[...]***
KeyPress event, serial 34, synthetic NO, window 0x1a00001,
    root 0xaa, subw 0x0, time 314970136, (690,-128), root:(692,257),
    state 0x0, **keycode 61** (keysym 0x2d, minus), same_screen YES,
    XLookupString gives 1 bytes: (2d) "-"
    XmbLookupString gives 1 bytes: (2d) "-"
    XFilterEvent returns: False
 
KeyRelease event, serial 34, synthetic NO, window 0x1a00001,
    root 0xaa, subw 0x0, time 314970205, (690,-128), root:(692,257),
    state 0x0, **keycode 61** (keysym 0x2d, minus), same_screen YES,
    XLookupString gives 1 bytes: (2d) "-"
    XFilterEvent returns: False
***[...]***
```
All right, so as an example, my minus key has the keycode **61**. The command '**xmodmap -pke**' will list all current keycodes and what they are bound to, but here we're only interested in 61. (Obviously, replace that with what your output shows.)
```
$ xmodmap -pke | grep 61
keycode  **61** = minus underscore minus underscore dead_belowdot dead_abovedot
keycode **161** =
```
As we **grep** the output for **61**, it will also obviously catch 1**61**, but just ignore that one. If you can't enter the pipe or bar character (**|**, which I imagine is the one you mean by vertical bar), just skip the grep part and scroll up to find your keycode.
 
Anyway, those words after the equality sign are **symbols**. The first one is the symbol that gets sent if you press the key normally (minus), the second one if pressed with shift (underscore). I think you have to enable extra modifiers for the third and fourth symbol. The fifth and sixth are when pressed with AltGr (dead_belowdot) and Shift+AltGr (dead_abovedot) respectively.
 
Many symbols are self-explanatory (a A b B minus plus quote backslash, etc), but for a list of more obscure ones, install the **x11proto-core-dev** package, then open up **/usr/include/X11/keysymdef.h** in a text editor.
 
So, let's try modifying it. Just assume keycode 61 is your slash/pipe key. I use a Swedish keyboard myself and I don't know what your keyboard layout is like, so I'm just guessing now.
```
$ xmodmap -e 'keycode 61 = backslash bar'
```
The changes should be immediate. If nothing happened, doublecheck that you have the right keycode. Try again with different symbols, or add more as you please. Remember that the third and fourth symbols likely need you to enable an extra modifier (beyond Shift, Alt, Control and AltGr), and the fifth and sixth need you to have an AltGr key. You can create a custom one, but I don't know the details on how to do that.
 
If you find a combination that works, save it to a script that gets run when you login. Such as **~/.kde/Autostart/fixkeys**;
```
#!/bin/bash
xmodmap -e 'keycode 61 = backslash bar'
```
Remember to set it as executable.
 
In the KDE version that's in the main maverick repositories (4.5.1), you can save the part inbetween the quotes to **~/.Xmodmap**, and upon logging in it will automatically run the xmodmap command on it and execute its contents.
```
keycode 61 = **backslash bar**
```
This functionality is broken in 4.5.85 and onwards, for which there's a bug entry [over on Launchpad]("https://bugs.launchpad.net/kubuntu-ppa/+bug/688515"). You can circumvent it by creating the startup script instead as above, or by creating another script that just executes the .Xmodmap file (which is the preferred behavior).
```
#!/bin/bash
xmodmap ~/.Xmodmap
```
 
Lastly, a real-life example. I rebound my Caps Lock key, since I never ever ever use it except when I hit it accidentally. It's now **F35** when hit normally, and normal Caps Lock if hit with Shift, just incase I still need it. Then I bound Yakuake to roll down when I hit F35. I picked such a high number just to avoid collisions. So my **~/.Xmodmap**;
```
keycode 66 = F35 Caps_Lock
```
 wow, nice explanation.

---

### Post by uauaua on 2011-06-24
i have change tab and also the caps lock.the tab keycode originally is keycode 23 and now;

KeyRelease event, serial 33, synthetic NO, window 0x4200001,
    root 0xa7, subw 0x0, time 3240944, (720,676), root:(724,787),
    state 0x0, keycode 23 (keysym 0xffe5,** Caps_Lock**), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False


then the caps lock keycode originally is keycode 66 and now:


KeyPress event, serial 33, synthetic NO, window 0x4200001,
    root 0xa7, subw 0x0, time 3255485, (720,676), root:(724,787),
    state 0x0, keycode 66 (keysym 0xff09, Tab), same_screen YES,
    XLookupString gives 1 bytes: (09) "    "
    XmbLookupString gives 1 bytes: (09) "    "
    XFilterEvent returns: False


but when i hit the tab, nothing happen
then when i hit the caps lock, it came out with caps lock and also tab..

can someone fix this???

---

### Post by uauaua on 2011-12-29
can u explain more about how to make it execute at start up in ubuntu 11.10. I am not understand

---

