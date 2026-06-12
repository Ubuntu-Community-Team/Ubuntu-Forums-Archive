---
title: "Genius tablet not working"
date: 2013-02-11
forum: Hardware
---

### Post by Jacques Duflos on 2013-02-11
Hello,
I have a Genius MousPen M508W graphic tablet and I am enable to make it work.

The mouse works, the buttons of the stylus work but not the stylus. In fact every thing works find except that the cursor does not move when I move around the stylus (it clics when I hit the tablet but pressure sensitivity does not seams to work).

I have tried to follow the instructions given in this thread [http://ubuntuforums.org/showthread.php?t=1337260](http://ubuntuforums.org/showthread.php?t=1337260) but it didn't work.

Here are few info :
```

$ grep -i name /proc/bus/input/devices
N: Name="Lid Switch"
N: Name="Power Button"
N: Name="Sleep Button"
N: Name="AT Translated Set 2 keyboard"
N: Name="Video Bus"
N: Name="Laptop Integrated Webcam"
N: Name="Dell WMI hotkeys"
N: Name="SynPS/2 Synaptics TouchPad"
N: Name="HDA Intel HDMI/DP,pcm=3"
N: Name="UC-logic 5x8 Table"
N: Name="UC-logic 5x8 Table"
N: Name="UC-logic 5x8 Table"

```(by the way why does my tablet appears three times ?)

```

$ cat /etc/hal/fdi/policy/99-x11-wizardpen.fdi
<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->

                <match key="info.product" contains="UC-logic 5x8 Table">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
                <merge key="input.x11_options.TopX" type="string">5619</merge>
                <merge key="input.x11_options.TopY" type="string">6554</merge>
                <merge key="input.x11_options.BottomX" type="string">29405</merge>
                <merge key="input.x11_options.BottomY" type="string">29671</merge>
                <merge key="info.product" type="string">stylus</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
                </match>
            </device>



            </deviceinfo>

``````

$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0bc2:5071 Seagate RSS LLC 
Bus 002 Device 003: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 005 Device 004: ID 5543:0522 UC-Logic Technology Corp.
``````
$ cat /usr/share/X11/xorg.conf.d/70-wizardpen.conf
Section "InputClass"
   Identifier "wizardpen"
# je modifie MatchIsTablet par MatchIsPointer comme decirt @
# http://ubuntuforums.org/showpost.php?p=9273383&postcount=10
# aucun effet constate
   MatchIsPointer "on"
   MatchDevicePath "/dev/input/event*"
   MatchProduct "WALTOP|Tablet"
#   MatchProduct "m508w"      ca, ca marche encore moins
   MatchTag "wizardpen"
   Driver "wizardpen"
   Option        "TopX"        "1506"
   Option        "TopY"        "2705"
   Option        "BottomX"    "31225"
   Option        "BottomY"    "30892"
EndSection

```Don't pay attention to the comments

Any ideas someone ?

---

### Post by Favux on 2013-02-11
Hi Jacques Duflos,

Welcome to Ubuntu forums!


First what release of Ubuntu are you using?  I am very puzzled to see a .fdi file along with a .conf file!

What is the output of the following terminal command?
```
xinput list
```

According to the DIGI*mend* project your tablet (except for the frame buttons?) is supported by the 3.5 kernel:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status)

---

### Post by Jacques Duflos on 2013-02-11
Hello Favux,
Thanks for the answer.
I am using Ubuntu 12.04

Here is the output you asked
```
$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech Unifying Device. Wireless PID:1025    id=9    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; Laptop Integrated Webcam                    id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys     

```For the .fdi and .conf co-existing, I assume it is result of many attempts form different forum pages I tried. (shame on me but I can't even figure out if I'm using KUbuntu or Lubuntu or what ? Hint : mine is all brown  looking)

For the SoursForge link you mentioned , I had witnessed the information yet, I'm unfamiliar with kernel versions. How can I check mine, and if needed how can I upgrade it ?

---

### Post by Favux on 2013-02-11
The **xinput list** output looks like you forgot to plug your table in.

What is the output of the following command in a terminal?
```
cat /etc/issue
```

Well the .fdi file shouldn't do anything unless you also installed HAL.  Did you?

---

### Post by Jacques Duflos on 2013-02-11
Hi Favux

[QUOTE=Favux]The xinput list output looks like you forgot to plug your table in.[/QUOTE]
Please don't tell anyone :-&
Here is the output with the tablet plugged in
```
$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=12    [slave  pointer  (2)]
&#9116;   &#8627; UC-logic 5x8 Table                          id=9    [slave  pointer  (2)]
&#9116;   &#8627; UC-logic 5x8 Table                          id=14    [slave  pointer  (2)]
&#9116;   &#8627; UC-logic 5x8 Table                          id=15    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; Laptop Integrated Webcam                    id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys   

```(here too, the tablet appears three times)

Here is the output you asked
```
$ cat /etc/issue
Ubuntu 12.04.2 LTS \n \l
```Did I install HAL ? I don't think so, I have no memory of it. How do I check ?

---

### Post by Favux on 2013-02-11
One event/device node is the stylus, one the mouse, and one the frame buttons.

You have Precise, 12.04.  If you have the KDE Desktop then it is Kubuntu Precise.

How did you install the WizardPen driver?  The WizardPen driver does not support a tablet mouse, only the stylus.  Do you have a tablet mouse?

Let's check what driver you are on.  If the .conf file isn't matching it will be evdev not Wizardpen.
```
xinput list-props 9
```
Assuming 9 is the stylus,  Otherwise try 14 or 15.  You can also determine the driver from your Xorg.0.log in /var/log.

---

### Post by Jacques Duflos on 2013-02-12
How did I install the driver ?
I added this line
ppa:doctormo/xorg-wizardpen
to the software sources as described here [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)
then I installed
```
sudo apt-get update
sudo apt-get install xserver-xorg-input-wizardpen
```

Do I have a tablet mouse ? well my tablet comes with a mouse and a stylus (the mouse works only on the tablet, but works well). Is this what you mean ?

Here are the outputs for 9, 14 and 15 (seeing the axis labels I guess 9 is actually the stylus)
```
$ xinput list-props 9
Device 'UC-logic 5x8 Table':
    Device Enabled (141):    1
    Coordinate Transformation Matrix (143):    1.000000, 0.000000,  0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (272):    0
    Device Accel Constant Deceleration (273):    1.000000
    Device Accel Adaptive Deceleration (274):    1.000000
    Device Accel Velocity Scaling (275):    10.000000
    Device Product ID (261):    21827, 1314
    Device Node (262):    "/dev/input/event4"
    Evdev Axis Inversion (276):    0, 0
    Evdev Axis Calibration (277):    <no items>
    Evdev Axes Swap (278):    0
    Axis Labels (279):    "Abs X" (376), "Abs Y" (377), "Abs Z" (572), "Abs Rotary X" (573), "Abs Pressure" (378)
    Button Labels (280):    "Button Left" (144), "Button Middle" (145),  "Button Right" (146), "Button Wheel Up" (147), "Button Wheel Down" (148)
    Evdev Middle Button Emulation (281):    0
    Evdev Middle Button Timeout (282):    50
    Evdev Third Button Emulation (283):    0
    Evdev Third Button Emulation Timeout (284):    1000
    Evdev Third Button Emulation Button (285):    3
    Evdev Third Button Emulation Threshold (286):    20
    Evdev Wheel Emulation (287):    0
    Evdev Wheel Emulation Axes (288):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (289):    10
    Evdev Wheel Emulation Timeout (290):    200
    Evdev Wheel Emulation Button (291):    4
    Evdev Drag Lock Buttons (292):    0
``````
$ xinput list-props 14
Device 'UC-logic 5x8 Table':
    Device Enabled (141):    1
    Coordinate Transformation Matrix (143):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (272):    0
    Device Accel Constant Deceleration (273):    1.000000
    Device Accel Adaptive Deceleration (274):    1.000000
    Device Accel Velocity Scaling (275):    10.000000
    Device Product ID (261):    21827, 1314
    Device Node (262):    "/dev/input/event11"
    Evdev Axis Inversion (276):    0, 0
    Evdev Axes Swap (278):    0
    Axis Labels (279):    "Rel X" (151), "Rel Y" (152), "Rel Horiz Wheel" (270)
    Button Labels (280):    "Button 0" (571), "Button Unknown" (264), "Button Unknown" (264), "Button Wheel Up" (147), "Button Wheel Down" (148), "Button Horiz Wheel Left" (149), "Button Horiz Wheel Right" (150)
    Evdev Middle Button Emulation (281):    0
    Evdev Middle Button Timeout (282):    50
    Evdev Third Button Emulation (283):    0
    Evdev Third Button Emulation Timeout (284):    1000
    Evdev Third Button Emulation Button (285):    3
    Evdev Third Button Emulation Threshold (286):    20
    Evdev Wheel Emulation (287):    0
    Evdev Wheel Emulation Axes (288):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (289):    10
    Evdev Wheel Emulation Timeout (290):    200
    Evdev Wheel Emulation Button (291):    4
    Evdev Drag Lock Buttons (292):    0
``````
$ xinput list-props 15
Device 'UC-logic 5x8 Table':
    Device Enabled (141):    1
    Coordinate Transformation Matrix (143):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (272):    0
    Device Accel Constant Deceleration (273):    1.000000
    Device Accel Adaptive Deceleration (274):    1.000000
    Device Accel Velocity Scaling (275):    10.000000
    Device Product ID (261):    21827, 1314
    Device Node (262):    "/dev/input/event10"
    Evdev Axis Inversion (276):    0, 0
    Evdev Axes Swap (278):    0
    Axis Labels (279):    "Rel X" (151), "Rel Y" (152), "Rel Horiz Wheel" (270), "Rel Vert Wheel" (271)
    Button Labels (280):    "Button Left" (144), "Button Middle" (145), "Button Right" (146), "Button Wheel Up" (147), "Button Wheel Down" (148), "Button Horiz Wheel Left" (149), "Button Horiz Wheel Right" (150), "Button Side" (265), "Button Extra" (266), "Button Unknown" (264), "Button Unknown" (264), "Button Unknown" (264), "Button Unknown" (264)
    Evdev Middle Button Emulation (281):    0
    Evdev Middle Button Timeout (282):    50
    Evdev Third Button Emulation (283):    0
    Evdev Third Button Emulation Timeout (284):    1000
    Evdev Third Button Emulation Button (285):    3
    Evdev Third Button Emulation Threshold (286):    20
    Evdev Wheel Emulation (287):    0
    Evdev Wheel Emulation Axes (288):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (289):    10
    Evdev Wheel Emulation Timeout (290):    200
    Evdev Wheel Emulation Button (291):    4
    Evdev Drag Lock Buttons (292):    0
```And here is a part of the /var/log/Xorg.0.log file (relevent I hope)
```
[   564.652] (II) config/udev: removing device Logitech Unifying Device. Wireless PID:1025
[   564.654] (II) evdev: Logitech Unifying Device. Wireless PID:1025: Close
[   564.654] (II) UnloadModule: "evdev"
[   564.655] (II) Unloading evdev
[   587.225] (II) config/udev: Adding input device UC-logic 5x8 Table (/dev/input/mouse0)
[   587.225] (II) No input driver specified, ignoring this device.
[   587.225] (II) This device may have been added with another device file.
[   587.227] (II) config/udev: Adding input device UC-logic 5x8 Table (/dev/input/event4)
[   587.227] (**) UC-logic 5x8 Table: Applying InputClass "evdev tablet catchall"
[   587.227] (II) Using input driver 'evdev' for 'UC-logic 5x8 Table'
[   587.227] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   587.227] (**) UC-logic 5x8 Table: always reports core events
[   587.227] (**) evdev: UC-logic 5x8 Table: Device: "/dev/input/event4"
[   587.227] (--) evdev: UC-logic 5x8 Table: Vendor 0x5543 Product 0x522
[   587.227] (--) evdev: UC-logic 5x8 Table: Found 3 mouse buttons
[   587.227] (--) evdev: UC-logic 5x8 Table: Found absolute axes
[   587.227] (--) evdev: UC-logic 5x8 Table: Found x and y absolute axes
[   587.227] (--) evdev: UC-logic 5x8 Table: Found absolute tablet.
[   587.227] (II) evdev: UC-logic 5x8 Table: Configuring as tablet
[   587.227] (**) evdev: UC-logic 5x8 Table: YAxisMapping: buttons 4 and 5
[   587.227] (**) evdev: UC-logic 5x8 Table: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   587.227] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/input/input10/event4"
```Evdev appearing everywhere, I guess it is the used one.

---

### Post by Favux on 2013-02-12
Correct it is on the evdev driver.  So you are either not matching to the WizardPen driver or it isn't active.  And apparently the stylus doesn't work with the evdev driver and won't until you get the fix in the 3.5 kernel.

Release 6 of the kernel patches has the fix backported for the Precise kernel according to the compatability file:  [http://digimend.git.sourceforge.net/git/gitweb.cgi?p=digimend/kernel-patches.git;a=blob_plain;f=COMPATIBILITY;hb=v6](http://digimend.git.sourceforge.net/git/gitweb.cgi?p=digimend/kernel-patches.git;a=blob_plain;f=COMPATIBILITY;hb=v6)
[http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Kernel_patches](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Kernel_patches)
[http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend#Drivers](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend#Drivers)
So you can either use the patch set or one of the pre-rolled kernels.
[http://ubuntuforums.org/showthread.php?t=1946486](http://ubuntuforums.org/showthread.php?t=1946486)

Or you could use the WizardPen driver which will lose you the mouse and frame buttons:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_setup_with_WizardPen](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_setup_with_WizardPen)
> I added this line
ppa:doctormo/xorg-wizardpen
to the software sources as described here [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)
then I installed
```
sudo apt-get update
sudo apt-get install xserver-xorg-input-wizardpen

```

Basically doing that installed two versions of WizardPen.  The PPA one and the one from the repositories.  Except I didn't think the Precise repository had WizardPen anymore or that the PPA had a version that would install on Precise.  So huh.  Did you get errors?

---

### Post by Jacques Duflos on 2013-02-14
I chose the patch solution. I followed every step of this thread
[http://ubuntuforums.org/showthread.php?t=1946486](http://ubuntuforums.org/showthread.php?t=1946486)
According to the time the computer spent working and the clean-up I had to do to free a little space on my disk, something has definitely been done.
However I can't see any modification of my tablet behaviour (even after multiple reboot).

[QUOTE=Favux]Basically doing that installed two versions of WizardPen.  The PPA one  and the one from the repositories.  Except I didn't think the Precise  repository had WizardPen anymore or that the PPA had a version that  would install on Precise.  So huh.  Did you get errors?     [/QUOTE]
I don't remember any error message when installing this. As it did not solve the problem, I did not insist.

---

### Post by Favux on 2013-02-14
> I chose the patch solution. I followed every step of this thread
[http://ubuntuforums.org/showthread.php?t=1946486](http://ubuntuforums.org/showthread.php?t=1946486)
According to the time the computer spent working and the clean-up I had to do to free a little space on my disk, something has definitely been done.
However I can't see any modification of my tablet behaviour (even after multiple reboot).
Sorry to hear that.  I know it was a lot of work.

Maybe you overlooked something when you adapted the instructions for the fifth patch set to the sixth patch set?  You might want to check that over.

You could always compile the WizardPen driver.  Then we just need to write a .conf file that matches your tablet to the driver.

---

### Post by Jacques Duflos on 2013-02-24
Hello again,
I don't have the required skills to understand what I did wrong but I finally came up with an easy [COLOR=Green]_[SIZE=3]solution : I upgraded to Ubuntu 12.10[/SIZE]_[/COLOR] and it works just find (any settings required).
Thanks for your time and answers, I learned a little about how does Linux work ;)

---

### Post by Jacques Duflos on 2013-02-25
OOuups, I've talked to early. Te pointer works but not the pressure (I've tried on gimp, blender and inkskape)

---

