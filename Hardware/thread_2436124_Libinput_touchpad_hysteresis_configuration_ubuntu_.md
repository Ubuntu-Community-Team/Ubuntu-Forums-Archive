---
title: "Libinput touchpad hysteresis configuration ubuntu 18.04.3"
date: 2020-01-31
forum: Hardware
---

### Post by andreberg on 2020-01-31
I've been trying to configure my touchpad without success. OS runs smoothly, except for a minor glitch on the touchpad.

Cursor movement is fine. However, when I stop and lift my finger from the touchpad, the mouse cursor will jump a bit on the direction I was moving the finger. This is very annoying when trying to select something, especially if it is a small button or selecting text, as it usually deselects a full line or selects an additional line. If I don't lift the finger from the touchpad there's no problem. As soon as I lift it, it jitters. I run Windows 7 on this same machine and this does not happen.

I've read extensively regarding libinput vs synaptics after going by serveral posts on the web that suggested installing the synaptics driver to fix several touchpad problems.

I understand that Synaptics was dropped from Ubuntu and that Libinput is the driver of choice and that it should work out of the box. I also read that Libinput dropped a lot of the fine tunning configurations and kept what most users would really change.

This is the result of xinput list
```
$ xinput list
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; Sony Vaio Jogdial                         id=8    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                id=13   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=6    [slave  keyboard (3)]
    &#8627; Sony Vaio Keys                            id=7    [slave  keyboard (3)]
    &#8627; Power Button                              id=9    [slave  keyboard (3)]
    &#8627; USB2.0 Camera: USB2.0 Camera              id=11   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard 
```
And this is the result of xinput list-props 13
```
$ xinput list-props 13
Device 'SynPS/2 Synaptics TouchPad':
        Device Enabled (165):   1
        Coordinate Transformation Matrix (167): 1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
        libinput Tapping Enabled (320): 1
        libinput Tapping Enabled Default (321): 0
        libinput Tapping Drag Enabled (322):    1
        libinput Tapping Drag Enabled Default (323):    1
        libinput Tapping Drag Lock Enabled (324):       0
        libinput Tapping Drag Lock Enabled Default (325):       0
        libinput Tapping Button Mapping Enabled (326):  1, 0
        libinput Tapping Button Mapping Default (327):  1, 0
        libinput Natural Scrolling Enabled (302):       1
        libinput Natural Scrolling Enabled Default (303):       0
        libinput Disable While Typing Enabled (328):    1
        libinput Disable While Typing Enabled Default (329):    1
        libinput Scroll Methods Available (308):        1, 1, 0
        libinput Scroll Method Enabled (309):   1, 0, 0
        libinput Scroll Method Enabled Default (310):   1, 0, 0
        libinput Click Methods Available (330): 1, 1
        libinput Click Method Enabled (331):    1, 0
        libinput Click Method Enabled Default (332):    1, 0
        libinput Middle Emulation Enabled (313):        0
        libinput Middle Emulation Enabled Default (314):        0
        libinput Accel Speed (315):     0.028040
        libinput Accel Speed Default (316):     0.000000
        libinput Left Handed Enabled (304):     0
        libinput Left Handed Enabled Default (305):     0
        libinput Send Events Modes Available (287):     1, 1
        libinput Send Events Mode Enabled (288):        0, 1
        libinput Send Events Mode Enabled Default (289):        0, 0
        Device Node (290):      "/dev/input/event4"
        Device Product ID (291):        2, 7
        libinput Drag Lock Buttons (306):       <no items>
        libinput Horizontal Scroll Enabled (307):       1
```
It shows I'm running the libinput driver, and no hysteresis config options available.

So, my first fix attempt was to install the synaptics driver as per suggested in some posts using sudo apt install xserver-xorg-input-synaptics
```
$ sudo apt install xserver-xorg-input-synpatics
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package xserver-xorg-input-synpatics
```

Oh surprise surprise!

Reading some more on these posts 

[https://askubuntu.com/questions/1031940/how-to-switch-from-libinput-to-synaptics-in-ubuntu-18-04](https://askubuntu.com/questions/1031940/how-to-switch-from-libinput-to-synaptics-in-ubuntu-18-04)
[https://askubuntu.com/questions/248914/what-is-hardware-enablement-hwe](https://askubuntu.com/questions/248914/what-is-hardware-enablement-hwe)

I thought, oh well, It must be that as I have the 18.04.3 version installed it won't find the old driver. So I went on and tried sudo apt install xserver-xorg-input-synaptics-dev-hwe-18.04 and got this
```
$ sudo apt install xserver-xorg-input-synaptics-dev-hwe-18.04
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  x11proto-core-dev x11proto-dev xorg-sgml-doctools
The following NEW packages will be installed:
  x11proto-core-dev x11proto-dev xorg-sgml-doctools
  xserver-xorg-input-synaptics-dev-hwe-18.04
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 274 kB of archives.
After this operation, 1.549 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://cl.archive.ubuntu.com/ubuntu bionic/main amd64 xorg-sgml-doctools all 1:1.11-1 [12,9 kB]
Get:2 http://cl.archive.ubuntu.com/ubuntu bionic/main amd64 x11proto-dev all 2018.4-4 [251 kB]
Get:3 http://cl.archive.ubuntu.com/ubuntu bionic/main amd64 x11proto-core-dev all 2018.4-4 [2.620 B]
Get:4 http://cl.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 xserver-xorg-input-synaptics-dev-hwe-18.04 all 1.9.1-1ubuntu1~18.04.1 [7.084 B]
Fetched 274 kB in 1s (221 kB/s)                                    
Selecting previously unselected package xorg-sgml-doctools.
(Reading database ... 273721 files and directories currently installed.)
Preparing to unpack .../xorg-sgml-doctools_1%3a1.11-1_all.deb ...
Unpacking xorg-sgml-doctools (1:1.11-1) ...
Selecting previously unselected package x11proto-dev.
Preparing to unpack .../x11proto-dev_2018.4-4_all.deb ...
Unpacking x11proto-dev (2018.4-4) ...
Selecting previously unselected package x11proto-core-dev.
Preparing to unpack .../x11proto-core-dev_2018.4-4_all.deb ...
Unpacking x11proto-core-dev (2018.4-4) ...
Selecting previously unselected package xserver-xorg-input-synaptics-dev-hwe-18.04.
Preparing to unpack .../xserver-xorg-input-synaptics-dev-hwe-18.04_1.9.1-1ubuntu1~18.04.1_all.deb ...
Unpacking xserver-xorg-input-synaptics-dev-hwe-18.04 (1.9.1-1ubuntu1~18.04.1) ...
Setting up xorg-sgml-doctools (1:1.11-1) ...
Processing triggers for sgml-base (1.29) ...
Setting up x11proto-dev (2018.4-4) ...
Setting up xserver-xorg-input-synaptics-dev-hwe-18.04 (1.9.1-1ubuntu1~18.04.1) ...
Setting up x11proto-core-dev (2018.4-4) ...
```
But when listing the pointer drivers it still shows I'm using the libinput ones.

Uninstalled the HWE driver with sudo apt remove xserver-xorg-input-synaptics-dev-hwe-18.04 and I'm back at the beginning.

I found these other threads regarding touchpad drivers and kernel version

[https://ubuntuforums.org/showthread.php?t=2432877&highlight=synaptics+touchpad](https://ubuntuforums.org/showthread.php?t=2432877&highlight=synaptics+touchpad)
[https://ubuntuforums.org/showthread.php?t=2432565](https://ubuntuforums.org/showthread.php?t=2432565)
[https://ubuntuforums.org/showthread.php?t=2433075&highlight=synaptics+touchpad](https://ubuntuforums.org/showthread.php?t=2433075&highlight=synaptics+touchpad)

Which suggest the issue might be the kernel version. So I run uname -a
I ran the following:
```
$ uname -a
5.3.0-28-generic #30~18.04.1-Ubuntu SMP Fri Jan 17 06:14:09 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
```
And I was surprised to find that I apparently I was not running 18.04.3,  which by the way is the image used to install Ubuntu on this machine  (SONY VAIO S Series).

I'm stuck here and would appreciate any help.

Is there a way to install the old synaptics driver for the touchpad? Alternatively, is there a way to configure hysteresis in the libinput driver?

Thanks

UPDATE:

Another day, another try.

Did
```
sudo apt update
```
which gave 12 packages for potential upgrade. Did not upgrade, but just went on to do "sudo apt install xserver-xorg-input-synaptics" which gave the following output
```
$ sudo apt install xserver-xorg-input-synaptics
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies
 xserver-xorg-input-synaptics : Depends: xserver-xorg-core (>= 2:1.18.99.901)
E: Unable to correct problems, you have held broken packages.
```
Then tried with the hwe version
```
sudo apt install xserver-xorg-input-synaptics-hwe-18.04
```
which ran smoothly. Then logged out and now I have the synaptics driver showing up as the driver for the touchpad and working. Let's dive into configuration now to solve my particular issue.

The driver installed two files into /usr/share/X11/xorg.conf.d/. One named "51-synaptics-quirks.conf" and another named "70-synaptics.conf". The first is related to some DELL and HP machines with issues on their touchpads. The second is the generic.

To avoid getting the synaptics driver being wiped-out during a future system upgrade and replaced with the libinput driver I copied the "70-synpatics.conf" file located in /usr/share/X11/xorg.conf.d/ to /etc/X11/xorg.conf.d and assigned it a higher priority by dropping the "70" to "10" so as to overide the libinput driver upon boot.

```
sudo mkdir /etc/X11/xorg.conf.d
```
as my system did not have that specific directory. Then
```
sudo cp /usr/share/X11/xorg.conf.d/70-synaptics.conf /etc/X11/xorg.conf.d/10-synaptics.conf
```

Now to configure hysteresis. If you do "xinput list-props X" where X is the number of the device, then you'll probably see that hysteresis does not show up on the listed definitions.

Using synclient which comes with the driver it's possible to twitch the configuration. To list current properties:
```
$ synclient -l
Parameter settings:
    LeftEdge                = 1607
    RightEdge               = 5335
    TopEdge                 = 1388
    BottomEdge              = 4464
    FingerLow               = 25
    FingerHigh              = 30
    MaxTapTime              = 180
    MaxTapMove              = 247
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    EmulateMidButtonTime    = 0
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = -112
    HorizScrollDelta        = 112
    VertEdgeScroll          = 1
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 0
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.0280405
    TouchpadOff             = 2
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 2
    RBCornerButton          = 3
    LTCornerButton          = 0
    LBCornerButton          = 0
    TapButton1              = 1
    TapButton2              = 3
    TapButton3              = 0
    ClickFinger1            = 1
    ClickFinger2            = 3
    ClickFinger3            = 0
    CircularScrolling       = 0
    CircScrollDelta         = 0.1
    CircScrollTrigger       = 0
    CircularPad             = 0
    PalmDetect              = 0
    PalmMinWidth            = 10
    PalmMinZ                = 200
    CoastingSpeed           = 20
    CoastingFriction        = 50
    PressureMotionMinZ      = 30
    PressureMotionMaxZ      = 160
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    ResolutionDetect        = 1
    GrabEventDevice         = 0
    TapAndDragGesture       = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    HorizHysteresis         = 8
    VertHysteresis          = 8
    ClickPad                = 1
    RightButtonAreaLeft     = 3471
    RightButtonAreaRight    = 0
    RightButtonAreaTop      = 4070
    RightButtonAreaBottom   = 0
    MiddleButtonAreaLeft    = 0
    MiddleButtonAreaRight   = 0
    MiddleButtonAreaTop     = 0
    MiddleButtonAreaBottom  = 0
```
which shows vert and horiz hysteresis values at 8.

I changed those values to something which suited me best by
```
synclient HorizHysteresis=25
synclient VertHysteresis=25
```
and now i have a touchpad working to my liking.

So, hope this helps someone in my same situation.

---

