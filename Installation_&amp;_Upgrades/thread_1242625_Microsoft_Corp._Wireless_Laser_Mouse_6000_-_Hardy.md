---
title: "Microsoft Corp. Wireless Laser Mouse 6000 - Hardy"
date: 2009-08-17
forum: Installation &amp; Upgrades
---

### Post by super kim on 2009-08-17
Hi,

 i have installed ubuntu 8.04 on my main hard drive as karmic and jaunty offer no support for my 'dated' ATI graphics card.

i have set up my wacom tablet and it works fine (thanks to Favux) i have still got a problem with my mouse.

the mouse is working on its most basic level in that the cursor tracks fine and the left/right click work. the scroll wheel has limited functionality though. i can scroll vertically but not horizontally. the scroll wheel button does not work. the 'extra' button on the left side does nothing too.

i booted with both karmic and jaunty, they automatically set up and use the extra features, except the 'extra' button (which has never done anything)

my xorg.conf is standard with regards to the mouse set up. is this where i need to tell hardy about the buttons?

---

### Post by LowSky on 2009-08-17
[https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)


hope this helps

---

### Post by Favux on 2009-08-17
Hi super kim,

In addition to LowSky's reference here's a wiki for the Microsoft Wireless Laser Mouse 6000:  [https://wiki.ubuntu.com/MicrosoftWirelessLaserMouse6000?highlight=(mouse](https://wiki.ubuntu.com/MicrosoftWirelessLaserMouse6000?highlight=(mouse))

Also a couple of Logitech mouse threads that have useful information:  [http://ubuntuforums.org/showthread.php?t=219894](http://ubuntuforums.org/showthread.php?t=219894)  and  [http://ubuntuforums.org/showthread.php?t=65471](http://ubuntuforums.org/showthread.php?t=65471)

Hope this is useful.

---

### Post by super kim on 2009-08-17
i have just changes my xorg and first try meant my mouse didnt work at all (good job the bamboo still worked lol) i tried again with this config:
```

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "gb"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
EndSection

Section "InputDevice"
  Identifier      "Evdev Mouse"
  Driver          "evdev"
  Option          "Name" " "Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00"
  Option          "evBits"  "+1-2"
  Option          "keyBits" "~272-287"
  Option          "relBits" "~0-2 ~6 ~8"
  Option          "Pass"    "3"
  Option          "CorePointer"
EndSection

Section "InputDevice"
    Identifier "stylus"
    Driver "wacom"
    Option "Device" "/dev/input/wacom"
    Option "Type" "stylus"
    Option "USB" "on" # USB ONLY
    Option "Button2" "2"  # make first button a middle button
    Option "Button3" "3"  # make second button a R button
EndSection

Section "InputDevice"
    Identifier "eraser"
    Driver "wacom"
    Option "Device" "/dev/input/wacom"
    Option "Type" "eraser"
    Option "USB" "on" # USB ONLY
EndSection

Section "InputDevice"
    Identifier "pad"
    Driver "wacom"
    Option "Device" "/dev/input/wacom"
    Option "Type" "pad"
    Option "USB" "on" # USB ONLY
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "fglrx"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    Defaultdepth    24
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    screen "Default Screen"
    InputDevice    "Evdev Mouse" "CorePointer"
    InputDevice "stylus" "SendCoreEvents"
    InputDevice "eraser" "SendCoreEvents"
    InputDevice "pad" # For Intuos3/CintiqV5/Graphire4/Bamboo tablets
EndSection

Section "Module"
    Load        "glx"
EndSection
```
and the graphics has failed??? and the extra buttons dont work either, i will revert to my backed up xorg and try that wiki link as it is specific to my mouse. excelent find Favux :D

---

### Post by super kim on 2009-08-17
hey Faxux it would of worked great but i found something out....

at first i thought i made a typo when i looked at the label on the mouse to discover it was in actual fact a 'Wireless Notebook Optical Mouse **4000**' it seems i got the 6000 from this:
```
~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 012: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 003 Device 007: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```thats why i got confused!

anyway i tried the steps anyway to see if anything worked since the difference is only 1 button. it kind of worked when i use the eye of gnome the thumb button moves right, unfortunately when i try to scroll up in firefox i go back and scrolling down goes forward :). i should be able to work it so the thumb button goes back and the scroll wheel works as they should then i can move on to get the horizontal scroll. cheers guys i'm well on the way to getting this sorted!

---

### Post by super kim on 2009-08-17
i have now done this......

changed the xorg to be:
```
 Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ExplorerPS/2"
        Option          "Buttons" "8"
        Option          "ZAxisMapping"          "4 5"
        Option          "ButtonMapping"         "1 2 3 6 7 8"
        Option          "Emulate3Buttons"       "false"
        Option          "Resolution"            "100"
EndSection 
```

installed "imwheel" through synaptics.

changed the imwheelrc to this:
```
".*"
None, Up, Up
None, Down, Alt_L|Left

"(null)"
None, Up, Up
None, Down, Alt_L|Left
```

then run this "$ exec imwheel -k -b "6 7 8" &" in a terminal.


the left, right click works still, the vertical scroll works still, but i haven't got horizontal scrolling yet i didn't expect to yet however i've had some success my thumb button now goes back with firefox yay

i don't know why the thumb button works as "down" but i will keep fiddling and trying things till i get buttons 6 and 7 to scroll left and right! i am trying to find out how imwheel works but i have a urge to try adding ```
Option          "YAxisMapping"          "6 7"
``` to the xorg.conf to see what happens, 

here i am again learning about things not drawing or surfing, linux really is a learning curve for me lol i spend my time learning how to get it to work how i want, and seem to never get round to doing what i want :lolflag:

---

### Post by Favux on 2009-08-17
Hi super kim,

Well it sounds like you have it working better than before anyway.

When you changed the Identifier and Driver (I never figured out why you were using Evdev) did you change the "ServerLayout" line to:
```
    InputDevice    "Configured Mouse"   "CorePointer"
```
to reflect the new Identifier?

---

### Post by super kim on 2009-08-17
hi Favux,

yes it is working better but still no response from the side scroll and button 3 doesn't work.
firstly i will post my xorg:
```

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "gb"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
EndSection

Section "InputDevice"
    Identifier "stylus"
    Driver "wacom"
    Option "Device" "/dev/input/wacom"
    Option "Type" "stylus"
    Option "USB" "on"
    Option "Button2" "2"
    Option "Button3" "3"
EndSection

Section "InputDevice"
    Identifier "eraser"
    Driver "wacom"
    Option "Device" "/dev/input/wacom"
    Option "Type" "eraser"
    Option "USB" "on"
EndSection

Section "InputDevice"
    Identifier "pad"
    Driver "wacom"
    Option "Device" "/dev/input/wacom"
    Option "Type" "pad"
    Option "USB" "on"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "fglrx"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    Defaultdepth    24
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen "Default Screen"
    InputDevice    "Configured Mouse" "CorePointer"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "pad"
EndSection

Section "Module"
    Load        "glx"
EndSection
```
secondly my imwheelrc:
```
".*"
None, Up, Button4
None, Down, Button5
None, Left, Button6
None, Right, Button7
None, Thumb2, Alt_L|Left
```

there is only one 'thumb' button but it seems to like being called "Thumb2"

in theory this should work, but this is not theory so it doesn't lol

i ran xev to see what x was picking up when i used the dead buttons and.... nothing, if there is no x event when i press/release these buttons then imwheel has no chance of executing the commands assigned to them.

jaunty and karmic have the mouse has buttons 5 and 6 (horizontal scroll) working fine, plug and play! why does the x not detect the button presses in hardy?

---

### Post by Favux on 2009-08-18
Hi super kim,

Why did you remove this whole chunk of the mouse section?:
```
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ExplorerPS/2"
        Option          "Buttons" "7"
        Option          "ZAxisMapping"          "4 5"
        Option          "ButtonMapping"         "1 2 3 6 7"
        Option          "Emulate3Buttons"       "false"
        Option          "Resolution"            "100"
EndSection 
```
The device input path and protocol are probably important.

---

### Post by super kim on 2009-08-18
> **Favux said:**
> Hi super kim,

Why did you remove this whole chunk of the mouse section?

i was just trying this tutorial [here]("http://ubuntuforums.org/showthread.php?t=787790")

i see no reason why it shouldn't be there though i'll stick it back and restart see if xev detects the buttons then

---

### Post by Favux on 2009-08-18
Hi super kim,

Well that explains it.  That looks like a good HOW TO.  Because Hardy included the change to Xserver 1.4 it's possible that older instructions (for Ubuntu versions prior to Hardy) on modmaps might have been rendered obsolete.

---

### Post by super kim on 2009-08-18
hey Faxuv,

i may be onto something here...
when i rebooted i noticed a syntax error on my part ```
Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver    "mouse"
    Option    "CorePointer"
    Option    "Device"        "/dev/input/mice"
    Option    "Protocol"        "ExplorerPS/2"
        Option    "Buttons"        "8"
        Option    "ZAxisMapping"        "4 5"
        Option    "ButtonMapping"        "1 2 3 6 7 8"
        Option    "Emulate3Buttons"    "false"
        Option    "Resolution"        "100"
EndSection
EndSection
```

which was amended then another reboot...
when i logged in i could only open the usb hard drive that was on the desktop, nothing else worked, i could click on the menus but whenever i opened 'terminal' it wouldn't open. i couldn't even log out. so i hit crtl_alt_backspace and logged in again, normal functions restored (phew)

heres the good news...
i opened a terminal and ran "xev" and now i get buttons all round!!!!!  i think i can set them up now that the x is seeing them and i even know what each button is called from xev's output. i will use the imwheelrc to set them up now.

---

### Post by Favux on 2009-08-18
Hi super kim,

Great!  Sounds like you're on the right track.

---

### Post by super kim on 2009-08-18
hi Favux, 

 i am getting this from xev
```

ButtonPress event, serial 28, synthetic NO, window 0x3400001,
    root 0x87, subw 0x0, time 1881763, (91,115), root:(765,166),
    state 0x10, button 7, same_screen YES

```however i spoke too soon i think. based on similar outputs from different button pressed i have determined that:
```
left        button 1
middle        button 2
right        button 3
up        button 4    
down        button 5
thumb        button 7
left-tilt    no output
right-tilt    no output
```which makes me think why does it not see the two tilt buttons, and where/what is button 6?

i want to try this for some reason:
```
        Option    "Buttons"        "10"
        Option    "ZAxisMapping"        "4 5"
        Option    "ButtonMapping"        "1 2 3 6 7 8 9 10"
```




that made no difference, i noticed that putting the options section back into the xorg.conf meant that button 3 was being detected i was hoping that the tilt wheel buttons might be 9 and 10. but no :(

i am going to try changing the ZAxisMapping see if that changes anything.

i am doing a complete system restart after i edit my xorg.conf, is this necessary? or can i just log out > log in?

---

### Post by Favux on 2009-08-18
Hi super kim,

Restarting X, ctrl-alt-backspace, should be enough, but rebooting probably doesn't hurt.

The HOW TO wasn't able to get wheel tilt working either.

---

### Post by super kim on 2009-08-18
no Favux, the tilt wheel is sill not being picked up by ubuntu at all. the other 6 buttons all get an event that i can see using 'xev' but nothing for the tilt. i'm running out of ideas now as i don't know what the x is exactly and i don't know how it works. i need to find this out so i can find out why jaunty recognises the tilt but hardy does not. i'm going to google x er i don't have a clue do i, dang it i might google xxx for fun :)8

---

### Post by Favux on 2009-08-18
Hi super kim,

Good luck!  It can get involved.  For example here is a page from the Xlibrary manual:  [http://tronche.com/gui/x/xlib/events/keyboard-pointer/keyboard-pointer.html#XButtonEvent](http://tronche.com/gui/x/xlib/events/keyboard-pointer/keyboard-pointer.html#XButtonEvent)  Basically at some point you need a, or to be, a coder.

---

### Post by super kim on 2009-08-18
> **Favux said:**
> Hi super kim,

Good luck!  It can get involved.  For example here is a page from the Xlibrary manual:  [http://tronche.com/gui/x/xlib/events/keyboard-pointer/keyboard-pointer.html#XButtonEvent](http://tronche.com/gui/x/xlib/events/keyboard-pointer/keyboard-pointer.html#XButtonEvent)  Basically at some point you need a, or to be, a coder.

hi Favux
i learn fast, and i have got some experience in html and a few other basic codes. i want to get this to work but it seems unlikely to be any time soon lol


heres where i am so far
```
$ xev | grep button
    state 0x10, button 1, same_screen YES
    state 0x110, button 1, same_screen YES
    state 0x10, button 2, same_screen YES
    state 0x210, button 2, same_screen YES
    state 0x10, button 3, same_screen YES
    state 0x410, button 3, same_screen YES
    state 0x10, button 4, same_screen YES
    state 0x810, button 4, same_screen YES
    state 0x10, button 5, same_screen YES
    state 0x1010, button 5, same_screen YES
    state 0x10, button 9, same_screen YES
    state 0x10, button 9, same_screen YES
    state 0x10, button 9, same_screen YES

```button 9 is the thumb button. 1,2,3,4, and 5 are all as expected left click, right click etc
still no recognition of the tilt wheel though. thanks for the link i might sleep before i read it (awake for 29 hours) as i'm too tired to try and learn heavy stuff lol

its nice that jaunty doesn't have this issue, i wish jaunty could give me the graphics card support though lol i hope the next LTS release will not forget all those older graphics cards as it's latest release (karmic) has limited support for my graphics card. 

:guitar:

i can also report this:
```
~$ hal-find-by-capability --capability "input.mouse" | xargs -n 1 hal-device
udi = '/org/freedesktop/Hal/devices/usb_device_45e_e1_noserial_if0_logicaldev_input'
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_45e_e1_noserial_if0'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:10.2/usb3/3-2/3-2.1/3-2.1:1.0/input/input8/event6'  (string)
  input.device = '/dev/input/event6'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_45e_e1_noserial_if0'  (string)
  info.product = 'Microsoft Microsoft Wireless Optical Mouse? 1.00'  (string)
  input.product = 'Microsoft Microsoft Wireless Optical Mouse? 1.00'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_45e_e1_noserial_if0_logicaldev_input'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  info.category = 'input'  (string)
  linux.subsystem = 'input'  (string)
  info.capabilities = { 'input', 'input.mouse' } (string list)
  linux.device_file = '/dev/input/event6'  (string)

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input'
  linux.sysfs_path = '/sys/devices/virtual/input/input0/event0'  (string)
  input.device = '/dev/input/event0'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Macintosh mouse button emulation'  (string)
  input.product = 'Macintosh mouse button emulation'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  info.category = 'input'  (string)
  linux.subsystem = 'input'  (string)
  info.capabilities = { 'input', 'input.mouse' } (string list)
  linux.device_file = '/dev/input/event0'  (string)

```

and this:
```
$ xinput query-state "Configured Mouse"
2 classes :
ButtonClass
    button[1]=up
    button[2]=up
    button[3]=up
    button[4]=up
    button[5]=up
    button[6]=up
    button[7]=up
    button[8]=up
    button[9]=up
    button[10]=up
    button[11]=up
    button[12]=up
    button[13]=up
    button[14]=up
    button[15]=up
    button[16]=up
    button[17]=up
    button[18]=up
    button[19]=up
ValuatorClass Mode=Relative Proximity=In
    valuator[0]=179
    valuator[1]=952

```

---

### Post by super kim on 2009-08-19
solved

well sort of, i did a clean install with jaunty. now the situation is much better the mouse has all buttons being recognized and they all do something!
1    leftclick
2    wheelclick
3    rightclick
4    wheelup
5    wheeldown
6    wheelleft
7    wheelright
9    thumb

now the thumb button will go forward in firefox and seems to do nothing in nautilus. i would like this to copy "Ctrl-c" in every instance except in the "eye of gnome" image viewer where i would like it to load the previous image in the directory.
the wheel button does nothing in firefox and nothing in nautilus. in the image viewer it will pan when an image is zoomed or larger than the window, i would like this to advance to the next image in the directory.

i have found many posts on how to configure the buttons but they seem to be irrelivant since all my buttons do something, and indeed in different applications. therfore i am sure there must be a way of editing this set up so i can change the functions. i should not need to install any keybinding sowtware because it already is doing so, just slightly wrong.

i may need to start this in a new thread since it is relating to a different version of ubuntu and the query is also different.

---

