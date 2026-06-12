---
title: "(Fujitsu Celsius H270)(18.04-LTS) Touchpad missing gestures"
date: 2022-10-04
forum: Hardware
---

### Post by csae2608 on 2022-10-04
Hello,

i have installed Ubuntu 18 LTS on rather old Fujitsu Laptop with Nvidia Quadro FX 770m Graphics.

The Ubuntu distro works fine,
only downside i noticed, is that it would not enable Touchpad Gestures for the Trackpad/Touchpad.

```
dmesg | grep psmouse
[    2.479460] psmouse serio4: synaptics: queried max coordinates: x [..5756], y [..5088]
[    2.506399] psmouse serio4: synaptics: Touchpad model: 1, fw: 7.0, id: 0x1c0b1, caps: 0xd04791/0xb02000/0x20000/0x0, board id: 0, fw id: 510125
[    2.506402] psmouse serio4: synaptics: serio: Synaptics pass-through port at isa0060/serio4/input0
[ 1091.201475] psmouse serio4: synaptics: queried max coordinates: x [..5756], y [..5088]


```

i tried to remedy by installing 

```
sudo apt install xserver-xorg-input-synaptics


```


however would yield

```
The following packages have unmet dependencies:
 xserver-xorg-input-synaptics : Depends: xserver-xorg-core (>= 2:1.18.99.901)
E: Unable to correct problems, you have held broken packages.

```

when trying to install "Xserver-xorg-core"
there may be  trouble ahead

```
sudo apt install xserver-xorg-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  amd64-microcode intel-microcode iucode-tool libglu1-mesa libxatracker2
  libxss1 libxvmc1 linux-generic-hwe-18.04 linux-headers-generic-hwe-18.04
  linux-image-generic-hwe-18.04 thermald x11-apps x11-session-utils xbitmaps
  xinit xinput
Use 'sudo apt autoremove' to remove them.
Suggested packages:
  xfonts-100dpi | xfonts-75dpi
The following packages will be REMOVED:
  ubuntu-desktop xorg xserver-xorg-core-hwe-18.04 xserver-xorg-hwe-18.04
  xserver-xorg-input-all-hwe-18.04 xserver-xorg-input-libinput-hwe-18.04
  xserver-xorg-input-wacom-hwe-18.04 xserver-xorg-video-all-hwe-18.04
  xserver-xorg-video-amdgpu-hwe-18.04 xserver-xorg-video-ati-hwe-18.04
  xserver-xorg-video-fbdev-hwe-18.04 xserver-xorg-video-intel-hwe-18.04
  xserver-xorg-video-nouveau-hwe-18.04 xserver-xorg-video-qxl-hwe-18.04
  xserver-xorg-video-radeon-hwe-18.04 xserver-xorg-video-vesa-hwe-18.04
  xserver-xorg-video-vmware-hwe-18.04
The following NEW packages will be installed:
  xserver-xorg-core
0 upgraded, 1 newly installed, 17 to remove and 0 not upgraded.
Need to get 1.351 kB of archives.
After this operation, 5.586 kB disk space will be freed.
Do you want to continue? [Y/n] n
Abort.

```


since i have Nvidia-340 i am asking if i can safely proceed to remove all those packages above to install "xserver-xorg-core" and further "xserver-xorg-input-synaptics"
without damaging the running system.


Thanks.

---

### Post by csae2608 on 2022-10-04
ok, i moved on to Ubuntu 20.04,

and was able to install [B]xserver-xorg-input-synaptics



[/B]but i am still missing touchpad gestures.

any suggestions?

thanks

---

### Post by csae2608 on 2022-10-11
synclient -l
Parameter settings:
    LeftEdge                = 1771
    RightEdge               = 5457
    TopEdge                 = 1665
    BottomEdge              = 4831
    FingerLow               = 25
    FingerHigh              = 30
    MaxTapTime              = 180
    MaxTapMove              = 248
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = -112
    HorizScrollDelta        = 112
    VertEdgeScroll          = 0
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 1
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.035417
    UpDownScrolling         = 1
    LeftRightScrolling      = 1
    UpDownScrollRepeat      = 1
    LeftRightScrollRepeat   = 1
    ScrollButtonRepeat      = 100
    TouchpadOff             = 0
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
    PalmDetect              = 1
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
    HorizHysteresis         = 28
    VertHysteresis          = 28
    ClickPad                = 0

---

### Post by csae2608 on 2022-10-11
another thing found out:

touchpad + gestures would correctly function on Ubuntu 14.04 + 16.04 , but touchpad gestures broken on 18.04+

there is installed Nvidia-340-driver propietary drivers.

---

