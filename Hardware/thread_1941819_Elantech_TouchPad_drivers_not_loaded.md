---
title: "Elantech TouchPad drivers not loaded"
date: 2012-03-16
forum: Hardware
---

### Post by kmas on 2012-03-16
I have a Samsung Series7 Chronos 14 inches. I installed a prestine Ubuntu 11.10 on it. I go to mouse and touchpad settings but the touchpad tab is missing. My mouse can right click and left click, i can even tap to click but i cant scroll, either using two fingers or using the right edge of the mouse. 

First mouse was detected as PS/2 Generic Mouse, I used [this]("http://ubuntuforums.org/showpost.php?p=8548795&postcount=4") to fix it. So now it is detected as Elantech touchpad. 

```
makezan@700Z3A:~$ xinput -list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Elantech Touchpad                      id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; WebCam SC-13HDL11431N                       id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
```

digging more into the touchpad, anyone know how to interpret this?? maybe I can force enable the right edge scroll for now. 
```
makezan@700Z3A:~$ xinput --list-props 12
Device 'PS/2 Elantech Touchpad':
    Device Enabled (131):    1
    Coordinate Transformation Matrix (133):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (249):    0
    Device Accel Constant Deceleration (250):    1.000000
    Device Accel Adaptive Deceleration (251):    1.000000
    Device Accel Velocity Scaling (252):    10.000000
    Evdev Axis Inversion (253):    0, 0
    Evdev Axes Swap (255):    0
    Axis Labels (256):    "Rel X" (141), "Rel Y" (142)
    Button Labels (257):    "Button Left" (134), "Button Middle" (135), "Button Right" (136), "Button Wheel Up" (137), "Button Wheel Down" (138)
    Evdev Middle Button Emulation (258):    0
    Evdev Middle Button Timeout (259):    50
    Evdev Wheel Emulation (260):    0
    Evdev Wheel Emulation Axes (261):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (262):    10
    Evdev Wheel Emulation Timeout (263):    200
    Evdev Wheel Emulation Button (264):    4
    Evdev Drag Lock Buttons (265):    0

```

But touchpad tab still missing.I tried synclient -l to see if options are enabled. But it says drivers not loaded.
```

makezan@700Z3A:~$ synclient -l
Couldn't find synaptics properties. No synaptics driver loaded?

```I check if the xorg driver is installed. It shows it is. 
```

makezan@700Z3A:~$ dpkg -l |grep syna
ii  xserver-xorg-input-synaptics           1.4.1-1ubuntu2                          Synaptics TouchPad driver for X.Org server

``` I tried [this launchpad bug]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/681904") but it still didn't fix the issues. I tried [this kubuntu thread ]("http://superuser.com/questions/136568/get-back-the-touchpad-scrolling-missing-in-kubuntu-10-04")

```
sudo modprobe -r psmouse sudo modprobe psmouse proto=imps sudo gedit /etc/modprobe.d/options   and adding the line:
  options psmouse proto=imps   Then close and reboot.

```It complained about options, not being a .conf file, I redid it with options.conf still no luck.

I tried[ this solution from ASUS]("http://ubuntuforums.org/showthread.php?t=1536264"), but no luck, or[ this fix from ALLure Groceries]("http://ubuntuforums.org/showpost.php?p=9175201&postcount=44") but the patch links are missing. plus those patches are from old kernels. 

this [community doc ]("https://help.ubuntu.com/community/SynapticsTouchpad#Enabling_True_Multitouch")links to a bug that breaks my dkms. and doesn't do it. 

the Samsung Series 9 guys too [have a fix ]("http://ubuntuforums.org/showpost.php?p=10709266&postcount=1")that didn't do it for me. 

I also [upgraded the kernel,]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.1-oneiric/") that broke the mouse completely. 
```
makezan@700Z3A:~$ uname -r
3.0.0-17-generic

```A while back I [fixed my mouse issues]("http://ubuntuforums.org/showthread.php?t=1586915") by getting a patch from a newer kernel and adding it through dkms. But I don't seem to find the patches I need, plus back then it was a real synaptic mouse, not elantech. 

Anyhelp?

Here are my devices, I am sure it is detecting it as a touchpad. but can't get synaptic to recognize that. 
```

makezan@700Z3A:~$ cat /proc/bus/input/devices

I: Bus=0011 Vendor=0002 Product=0001 Version=0000
N: Name="PS/2 Elantech Touchpad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input11
U: Uniq=
H: Handlers=mouse0 event4 
B: PROP=0
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3


```

---

### Post by glutama on 2012-03-17
I have this problem too, on the new Samsung Series 9. My computer also recognizes the pad as a PS/2 Elantech Touchpad, synclient also shows no syanptics drivers loaded, and there is no Touchpad tab in the Mouse properties and thus no 2 finger scrolling--a minor flaw in an otherwise excellent installation with kernel version 3.0.0.12-generic on Ubuntu 11.10.

---

### Post by glutama on 2012-03-18
bump :confused:

---

### Post by kmas on 2012-03-19
Hmm, I'm not sure we will ever get this answered. My fix was to install 12.04. Upgrading didn't do it. I also tried a 32 bit just to make sure it wasn't an architecture only issue. 12.04 comes with annoying issues, I will make a new thread about it and post my findings as soon as i'm done.

---

### Post by kmas on 2012-03-19
> **glutama said:**
> bump :confused:

check this thread out for different fixes for the same device. [http://ubuntuforums.org/showthread.php?t=1935699](http://ubuntuforums.org/showthread.php?t=1935699)

---

