---
title: "Packard Bell Easynote W8"
date: 2009-09-10
forum: Hardware
---

### Post by irne.barnard on 2009-09-10
I've got Ubuntu 8 installed successfully (9 states it's got some hangups with my graphics card, so I didn't even try). The H/W is as follows:

[LIST=1]
[*] ATI Mobility Radeon X1600 (**works**)
[*]Intel(R) PRO/Wireless 3945ABG Net (**works**)
[*]Intel(R) PRO/100 VE Net (**works**)
[*]1394 Net (**don't work**)
[*]NEC DVD RW ND-6750ASynaptics PS/2 Port TouchPad (**works**)
[*]Logitech Wireless Mobile mouse (**works**)
[*]Nokia E65 as internet connection device (**works**)
[*]HDAUDIO Soft Data Fax Modem with SmartCP (**don't work**)
[*]Realtek High Definition Audio (**works**)
[/LIST]
I'm not worried about the 2 devices not working above as I have never used them at all. Screen res is perfect at 1440x900 and OpenGL seems to work correctly. What does give me problems is the special keys. There's 2 in particular:

[LIST]
[*]The Wireless on/off button in the front, very important to keep battery life up when not needed to connect wirelessly
[*]The ECO button next to the power switch, boosts battery life by turning the graphics card, cpu, fanspeed & LCD backlight down.
[*]The multimedia touch buttons aren't important to me, but they also don't work :rolleyes:
[/LIST]
So I went through the KeyTouch manuals and ran the getscancodes utility (as per this thread [http://ubuntuforums.org/showthread.php?p=6114189#post6114189](http://ubuntuforums.org/showthread.php?p=6114189#post6114189)). None of the events in the /dev/input show anything whatsover. And to make life a real pain, whenever I run the getscancodes all keyboard access is suspended throughout, mouse clicks are dead, the only button working at all is the power on/off :lol: which means I've got to restart after every event# test ... not fun ... not fun at all!

Anyone have an idea what I did wrong? Or if I'm missing something?

---

### Post by irne.barnard on 2009-11-03
No-one have an idea? This is still bugging me.

---

