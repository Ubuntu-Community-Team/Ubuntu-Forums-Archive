---
title: "disabling tapping on touchpad"
date: 2011-12-29
forum: Hardware
---

### Post by iuval on 2011-12-29
I have an LT27 Gateway notebook. Not sure what the touchpad is. When I had Windows, I was able to disable the tapping on the touchpad, so that I could type without random redirection of the cursor due to spurious tapping signals from the touchpad. But since I got Lubuntu about a week ago, I have been unable to disable the tapping feature, which makes typing a challenge. I've searched this forum for solutions, and tried a few but nothing has worked so far. Some of the proposed solutions seem a bit too complicated for my unix knowledge. The synaptiks utility doesn't seem to do anything. I also tried installing and running gpointing-device-settings and disabling scrolling and tapping for an ALPS/PS-2 touchpad (is that what I have?) from there, but no effect after reboot.

All advice appreciated.

---

### Post by iuval on 2011-12-29
I also tried modifying touchpad-config.json. which I found in a .config/synaptiks directory, with MaxTapTime=0, but that got overwritten upon reboot. That file does respond to the changes I make from the synaptiks gui, but those changes don't seem to affect the touchpad. Also, i don't think it's related to my fingers brushing over the touchpad. Some noise from the keyboard maybe looking like a touchpad signal.

---

### Post by SteveDee on 2011-12-29
> **iuval said:**
> ...When I had Windows, I was able to disable the tapping on the touchpad...

You may be able to control your mouse pad using the Synaptic command: synclient.

If you type in a lxterminal:-
```

synclient

```
...you should see a list of parameter with their current values something like this:-
```

steve@Steve-Dell-D600:~$ synclient
Parameter settings:
    LeftEdge                = 153
    RightEdge               = 870
    TopEdge                 = 115
    BottomEdge              = 652
    FingerLow               = 12
    FingerHigh              = 14
    FingerPress             = 127
    MaxTapTime              = 180
    MaxTapMove              = 56
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 139
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 25
    HorizScrollDelta        = 25
    VertEdgeScroll          = 1

```
...if so, then when you type in:-
```

synclient TouchPadOff=1

```
...your mouse should stop responding. Now use the up-arrow (still in the terminal) to repeat the command, but change the value to 0
```

synclient TouchPadOff=0

```
...hopefully your mouse is responding again!

If this works then its time to bind a couple of key combinations to these commands.

Open your /home/iuval/.config/openbox/lubuntu-rc.xml file using the text editor.

Move through the file until you find:-
```

   <!-- Keybindings for Multimedia Keys and LCD Backlight (alternative when not using gnome-power-manager or xfce4-volumed)
     <keybind key=

```
...and add this section on new (clear) lines just above, like this:-
```

     <keybind key="C-F5">
      <action name="Execute">
        <command>synclient TouchPadOff=0</command>
      </action>
    </keybind>

     <keybind key="C-F6">
      <action name="Execute">
        <command>synclient TouchPadOff=1</command>
      </action>
    </keybind>

   <!-- Keybindings for Multimedia Keys and LCD Backlight (alternative when not using gnome-power-manager or xfce4-volumed)
     <keybind key=

```

Now logout and login again.
You should find that <ctrl><F6> disables your mouse pad, while <ctrl><F5> enables it.

You have basically added these new key-bindings between the tags <keyboard> & </keyboard>.
You should be able to see how to change these keys (you may prefer other combinations) and you can create more bindings in a similar fashion.

---

### Post by iuval on 2011-12-29
Thanks for that response. Unfortunately, my mouse pad did not stop responding when I typed in:
synclient TouchPadOff=1

It may not think it's a touchpad, but a regular mouse?

---

### Post by iuval on 2011-12-29
I already have a binding to turn off the touchpad--it is Fn F7. I suppose I can do that for now, though a better solution would be to just turn off tapping.

---

### Post by Rodney9 on 2011-12-29
> **SteveDee said:**
> You may be able to control your mouse pad using the Synaptic command: synclient.

If you type in a lxterminal:-
```

synclient

```
...you should see a list of parameter with their current values something like this:-
```

steve@Steve-Dell-D600:~$ synclient
Parameter settings:
    LeftEdge                = 153
    RightEdge               = 870
    TopEdge                 = 115
    BottomEdge              = 652
    FingerLow               = 12
    FingerHigh              = 14
    FingerPress             = 127
    MaxTapTime              = 180
    MaxTapMove              = 56
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 139
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 25
    HorizScrollDelta        = 25
    VertEdgeScroll          = 1

```
...if so, then when you type in:-
```

synclient TouchPadOff=1

```
...your mouse should stop responding. Now use the up-arrow (still in the terminal) to repeat the command, but change the value to 0
```

synclient TouchPadOff=0

```
...hopefully your mouse is responding again!

If this works then its time to bind a couple of key combinations to these commands.

Open your /home/iuval/.config/openbox/lubuntu-rc.xml file using the text editor.

Move through the file until you find:-
```

   <!-- Keybindings for Multimedia Keys and LCD Backlight (alternative when not using gnome-power-manager or xfce4-volumed)
     <keybind key=

```
...and add this section on new (clear) lines just above, like this:-
```

     <keybind key="C-F5">
      <action name="Execute">
        <command>synclient TouchPadOff=0</command>
      </action>
    </keybind>

     <keybind key="C-F6">
      <action name="Execute">
        <command>synclient TouchPadOff=1</command>
      </action>
    </keybind>

   <!-- Keybindings for Multimedia Keys and LCD Backlight (alternative when not using gnome-power-manager or xfce4-volumed)
     <keybind key=

```

Now logout and login again.
You should find that <ctrl><F6> disables your mouse pad, while <ctrl><F5> enables it.

You have basically added these new key-bindings between the tags <keyboard> & </keyboard>.
You should be able to see how to change these keys (you may prefer other combinations) and you can create more bindings in a similar fashion.

Thank You So Much

Works perfectly on my Toshiba laptop

Rodney

---

