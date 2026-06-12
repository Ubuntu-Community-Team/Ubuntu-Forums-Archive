---
title: "Mouse movement freezes the system"
date: 2011-11-17
forum: Hardware
---

### Post by Neill_R on 2011-11-17
Hi

I have solved the problem by obtaining another second hand PC with a Nvidia Geforce Fx 5700 AGP DVI and VGA ported card. i also get a PC that can handle 3GB rather than 2GB of ram.
------------------------------------------------------------------------------------------------------------------------------

I WOULD HAVE LIKE TO BEEN ABLE TO SOLVE THIS PROBLEM WITH THE S3 CARD but it seems no-one knows how...

====================================================================================

I am having to construct an xorg.conf file because my hardware is really old.

I am using 10.04.3 LTS because this give one the option to run X in low resolution mode.

this was an earlier thread 

[http://ubuntuforums.org/showthread.php?t=1881197](http://ubuntuforums.org/showthread.php?t=1881197) 

I have uploaded the xorg.conf and a screen shot showing that the two screen are not at same resolution.
1024 x 768. 

if i move the mouse, it will move, but then freezes.[COLOR=Red] Is the different screen resolutions any thing to do with this?[/COLOR]
I have to <alt>+<SysRq>+"R" "E" "I" "S" "U" "B" in order to reboot the PC.

Hardware PACKARD BELL IMEDIA 1328/1 2GB RAM 500GB HD Motherboard VGA (SIS) graphics.

+ old s3 Diamond Stealth 64 PCI VGA card.

If the Diamond stealth card is inset it become the BIOS Boot device. However if I do not swap the use of the cards around the display is totally distorted.

I am googling all the time to find a solution but as regards to X I am a complete novice

[COLOR=Red]Need some kind person to help please[/COLOR]

---

### Post by Neill_R on 2011-11-18
From my system running in low resolution mode (recovery console boot option)
just moving the mouse without clicking ant button and the system freezes. 

~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ImExPS/2 Generic Explorer Mouse             id=9    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=10    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=8    [slave  keyboard (3)]
~$ 

from my xorg.conf file


Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

The mouse is working in low resolution mode. How do I ensure that it is the same set-up as above?

---

### Post by Neill_R on 2011-11-19
sort of solved

---

