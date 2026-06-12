---
title: "set core pointer via script"
date: 2014-07-13
forum: Hardware
---

### Post by XylophoneTeeth on 2014-07-13
This is regards to Quantal with XFCE

I'm in the process of trying to make a script to perform some setup actions on GIMP and other applications.
In this, I need to be able to temporarily switch the core pointer device from the mouse to the wacom tablet.  
The idea is that I would then be able to use **xdotool** to set GIMP tools for both the mouse and wacom.

One attempted method was simply to use **xinput**:

```
fahrekin@bacon:~$ xinput | grep pointer
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Kensington      Kensington Expert Mouse     id=8    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Graphire3 stylus                      id=9    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Graphire3 eraser                      id=11    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Graphire3 cursor                      id=12    [slave  pointer  (2)]

fahrekin@bacon:~$ xinput --set-pointer 9
X Error of failed request:  XI_BadDevice (invalid Device parameter)
  Major opcode of failed request:  147 (XInputExtension)
  Minor opcode of failed request:  12 (X_ChangePointerDevice)
  Device id in failed request: 0x17
  Serial number of failed request:  20
  Current serial number in output stream:  20

fahrekin@bacon:~$ xinput --set-pointer "Wacom Graphire3 stylus"
X Error of failed request:  XI_BadDevice (invalid Device parameter)
  Major opcode of failed request:  147 (XInputExtension)
  Minor opcode of failed request:  12 (X_ChangePointerDevice)
  Device id in failed request: 0x17
  Serial number of failed request:  20
  Current serial number in output stream:  20
```

Using the **--set-pointer** option does not appear to work for any parameter, nor does the manpage for **xinput** give hope that it would for xorg-server 1.12 in X11R7.7.

> --set-pointer device
        Switch device in core pointer.  This option does nothing on X servers 1.5 and later

The second method I attempted was to use **xsetpointer**

```
fahrekin@bacon:~/bin$ xsetpointer -l | grep Pointer
2: "Virtual core pointer"    [XPointer]
4: "Virtual core XTEST pointer"    [XExtensionPointer]
8: "Kensington      Kensington Expert Mouse"    [XExtensionPointer]
9: "Wacom Graphire3 stylus"    [XExtensionPointer]
11: "Wacom Graphire3 eraser"    [XExtensionPointer]
12: "Wacom Graphire3 cursor"    [XExtensionPointer]

fahrekin@bacon:~/bin$ xsetpointer 9
Extended device 9 not found

fahrekin@bacon:~/bin$ xsetpointer "Wacom Graphire3 stylus"
Extended device Wacom Graphire3 stylus not found
```

... and it seems that **xsetpointer** doesn't appear to work like any example I've found online

_So, to anyone who might know, my questions are three:_
1: Am I doing something wrong in either case?
2: Is **xsetpointer** simply broken for the same particular reason that **xinput --set-pointer** does not work?
3: Is there another way to select the pointer device via a bash script?

Thanks in advance

---

### Post by XylophoneTeeth on 2014-07-16
Failing that, can anyone recommend an active forum or community which may be able to help?

---

### Post by Toz on 2014-07-16
You might be able to do this with Xfce's built in xfconf-query commands. Unfonrtuately, I don't have a wacom tablet to check this out for you but I can offer some suggestions for you to find out.

First, can you change the core pointer by going to Settings Manager >> Mouse and Touchpad?

Also, what does the following command return on your system?
```
xfconf-query -c pointers -lv
```

---

### Post by XylophoneTeeth on 2014-07-16
Perhaps i should clarify.  Generally speaking, there is no necessity that the alternative pointing device be a wacom.  It could easily be a touchpad or a second mouse.  All that is important is that the script is able to make X think a different device is active.  The settings under Mouse and Touchpad (as far as I understand it) merely define the cursor behavior for the different devices; this configurator doesn't have any means to set which device the core pointer device refers to.  

For instance:
in reference to the prior device configuration:

```
fahrekin@bacon:~$ xinput | grep pointer
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Kensington      Kensington Expert Mouse     id=8    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Graphire3 stylus                      id=9    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Graphire3 eraser                      id=11    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Graphire3 cursor                      id=12    [slave  pointer  (2)]
```

the core pointer [2] refers to the Kensington Mouse [8]:

```
fahrekin@bacon:~$ xinput -list --long | head -n 4
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
    Reporting 5 classes:
        Class originated from: 8. Type: XIButtonClass
        Buttons supported: 12
```

but if i bump the tablet momentarily, [2] refers to [9]:

```
fahrekin@bacon:/etc/cron.hourly$ xinput -list --long | head -n 4
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
    Reporting 7 classes:
        Class originated from: 9. Type: XIButtonClass
        Buttons supported: 12
```

... and now the particular settings being utilized from either the "Mouse and Touchpad" configurator or GIMP have changed appropriately.  
Of course, i can't make a script pick up the stylus and touch the wacom. 
(... actually, i could, but let's not go there)

I'm not sure there would normally be anything under xfconf that could do this.  
I don't have a 'pointers' channel on my setup, so your command as suggested returns 0 lines
however, these are the channels that are present:

```
fahrekin@bacon:~$ xfconf-query -l
Channels:
  thunar-volman
  xsettings
  xfce4-power-manager
  xfce4-settings-editor
  xfce4-mixer
  xfce4-keyboard-shortcuts
  xfce4-desktop
  xfwm4
  keyboards
  keyboard-layout
  xfce4-session
  xfce4-panel
  xfce4-mime-settings
```

and the likely place, 'xsettings', holds no properties that appear to be relevant:

```
fahrekin@bacon:~$ xfconf-query -c xsettings -l
/Gtk/ButtonImages
/Gtk/CanChangeAccels
/Gtk/ColorPalette
/Gtk/CursorThemeName
/Gtk/CursorThemeSize
/Gtk/FontName
/Gtk/IconSizes
/Gtk/IMModule
/Gtk/IMPreeditStyle
/Gtk/IMStatusStyle
/Gtk/KeyThemeName
/Gtk/MenuBarAccel
/Gtk/MenuImages
/Gtk/ToolbarIconSize
/Gtk/ToolbarStyle
/Net/CursorBlink
/Net/CursorBlinkTime
/Net/DndDragThreshold
/Net/DoubleClickDistance
/Net/DoubleClickTime
/Net/EnableEventSounds
/Net/EnableInputFeedbackSounds
/Net/IconThemeName
/Net/SoundThemeName
/Net/ThemeName
/Xft/Antialias
/Xft/Hinting
/Xft/HintStyle
/Xft/RGBA

```

like the Mouse dialog, these are just configuration items.
I would figure that the desired function would have to be performed at some level below the DE or WM.
Short of getting X to neatly switch devices, there might be some dirty way to force it by manipulating device availability at a lower level, but i'm just grasping there.

_EDIT:_
Thinking about input device handling for a bit, I began to grow unsure as to whether what I wanted to do would even be possible, as there exists only one XTEST virtual device for each master (and I'm not quite sure how all this works).  As my ultimate goal here is to use xdotool to issue fake click events for both the mouse and tablet, I performed a simple proof of concept experiment to test the persistence and uniqueness of device selection:

```
xdotool search --screen 0 --name "GIMP" windowfocus; 
sleep 0.1; xdotool mousemove 200 200
sleep 0.1; xdotool click 1
sleep 0.1; xdotool getmouselocation

```

running this script will focus the main GIMP window, move the cursor, and click the active pointing device's first button (left click)
depending on which pointing device was the last to produce any events (as described above), GIMP treats the click event as an action with the tool associated with that particular physical device.  This at least tells me that xdotool will perform as I intend.  All I need to do is what I've discussed prior.

---

