---
title: "How I setup my Bosto Kingtee 14wa version 2, on Ubuntu 14.04"
date: 2014-12-07
forum: Hardware
---

### Post by teage3 on 2014-12-07
For one Monitor BOSTO_14wa version 2 on Ubuntu 14.04

1-Download Driver from here >>> [https://github.com/lesliev/bosto_14wa](https://github.com/lesliev/bosto_14wa)
2-Compile and install the driver following the instructions in the README.md

3-Set the Bosto as the active display and uncheck the active of your current display using ArandR

Notes:
    Worked flawless on my HP-g65 laptop but, on my HP Compaq nc8430 I had to make some tweaks.

For HP Compaq nc8430:

Resolution problems. 

1024x768
800x600
848x480
640x480

This was my only options and was no good. The resolution I needed was 1366x768!!

Changing the resolution:

using xrandr in a terminal with these commands,

cvt 1366 768

Output from that command would look like this......
teage@nc8430:~$ cvt 1366 768
# 1368x768 59.88 Hz (CVT) hsync: 47.79 kHz; pclk: 85.25 MHz
Modeline "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync

Then, copy the information after the word “Modeline” into the XRandR command:

xrandr --newmode "1368x768_60.00" 85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync

Now you need to add the new mode like this........
xrandr --addmode VGA-0 1368x768_60.00

Your Monitor may differ from mine. Mine is labled as VGA-0. To find the name of your just use Arandr to find the name.

Thats all to get up and running ;)

If you are like me though, that is not enough. You want to map it to the right so you can have dual monitor setup!

PART 2--DUAL MONITOR WITH THE BOSTO KINGTEE 14_wa

Finding your device.

Open a terminal and enter--->    xinput --list

You will see something like this......
teage@nc8430:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Bosto Kingtee 14WA                          id=13    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=15    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                          id=16    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; SONiX Key Roll                              id=11    [slave  keyboard (3)]
    &#8627; SONiX Key Roll                              id=12    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=14    [slave  keyboard (3)]
    &#8627; HP WMI hotkeys                              id=17    [slave  keyboard (3)]
teage@nc8430:~$ 

We need the id of our Bosto which in my case is 13.

Now we map it to VGA-0 like by entering --->   xinput --map-to-output 13 VGA-0

THATS IT!! Sweetness!


NOTES:

Upon rebooting I noticed all my settings had been reset. I have spent hours trying to learn udev rules and failed. So I wrote a simple script to load everytime I plug my bosto in.
I placed my script which I call (setbosto) in /usr/local/bin The contents of (setbosto) are: 

#!/bin/bash 

#bosto monitor settings 
xrandr --newmode "1368x768_60.00" 85.25 1368 1440 1576 1784 768 771 781 798 -hsync +vsync xrandr --addmode VGA-0 1368x768_60.00 
xrandr --output VGA-0 --mode 1368x768_60.00 --right-of LVDS 
xinput --map-to-output 13 VGA-0 

Im running xubuntu, so to make this work I go to settings manager, removable drives and media, click on the input devices tab, then under tablet where it says (command I just enter the name of my script (setbosto). 

Not what I wanted but it works. I wanted to load my settings at boot. Doing so like this you will have to wait for your desktop to load then unplug the usb connection and plug it back in. 

Also, you will have to make the script executable once its writen. 
Sometimes the id changes so xinput --map-to-output 13 VGA-0 might be xinput --map-to-output 11 VGA-0 which is kind of annoying but its the best i can do at the moment.

---

