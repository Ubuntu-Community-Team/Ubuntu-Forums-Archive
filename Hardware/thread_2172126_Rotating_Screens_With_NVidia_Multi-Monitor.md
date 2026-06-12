---
title: "Rotating Screens With NVidia Multi-Monitor"
date: 2013-09-03
forum: Hardware
---

### Post by Olinga_Abbott on 2013-09-03
[TABLE]
[TR]
[TD="class: votecell"][/TD]
[TD="class: postcell"]                I'm having a problem with screen rotation. The relevant  configuration info I can think of is at the end of this message. I run  GNOME not Unity. The xorg.conf, or one very similar to it, worked for  several years until May of this year when I moved and needed to use a  single-monitor configuration for awhile. I tried returning to my  three-monitor configuration but the right two monitors are rotated and I  can't seem to get the nvidia driver to pay attention to the "Option  "Rotate" "left"" directive. So far I've tried:

[LIST=1]
[*]Disabling xinerama in ServerLayout, adding "Option "RandRRotation" "on"" directive to the two rotated screens (both on the same NVidia card). This results in a proper rotation the two screens but leads to more problems. The two NVidia screens are in TwinView mode, so windows maximize across both screens, I can't see the top or bottom of the right side of the window because the screens are very different resolutions, the Intel screen seems to run it's own GNOME session with the default configuration which I can use the same mouse cursor on but cannot move Windows onto (it has it's own GNOME panels), and dialog boxes are split down the middle between the two NVidia screens. 
[*]After #1, changing the TwinView setting in the NVidia Server Settings app. The screens become unrotated again. 
[*]Changing rotation in the Display applet. This is only possible when the NVidia screens are already in TwinView mode. Otherwise the applet never starts, reporting "RANDR extension is not present". Same result when using randr from the command line. 
[*]Placing "Option "Rotate" "(Left/Right)" in Device and Screen sections. 
[*]Replacing "(Left/Right)" with "(CW/CCW)"
[*]Replacing "(Left/Right)" with "(left/right)" 
[/LIST]
The most likely culprit I can think of is system updates occurring since May. Unfortunately I have no idea what else to try.[/TD]
[/TR]
[/TABLE]
```
$ cat /etc/*-release;sudo lspci|grep VGA;cat /proc/version;cat /etc/X11/xorg.conf
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.3 LTS"
NAME="Ubuntu"
VERSION="12.04.3 LTS, Precise Pangolin"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu precise (12.04.3 LTS)"
VERSION_ID="12.04"
3:00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
21:01:00.0 VGA compatible controller: NVIDIA Corporation G96 [GeForce 9500 GT] (rev a1)
Linux version 3.2.0-52-generic (buildd@roseapple) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #78-Ubuntu SMP Fri Jul 26 16:21:44 UTC 2013
Section "Files"
  ModulePath   "/usr/lib/xorg/modules"
  FontPath     "/usr/share/fonts/X11/misc"
  FontPath     "/usr/share/fonts/X11/cyrillic"
  FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
  FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
  FontPath     "/usr/share/fonts/X11/Type1"
  FontPath     "/usr/share/fonts/X11/100dpi"
  FontPath     "/usr/share/fonts/X11/75dpi"
  FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
  FontPath     "built-ins"
EndSection

Section "Monitor"
  Identifier   "Monitor0"
  VendorName   "Monitor Vendor"
  ModelName    "Monitor Model"
EndSection

Section "Monitor"
  Identifier   "Monitor1"
  VendorName   "Monitor Vendor"
  ModelName    "Monitor Model"
EndSection

Section "Monitor"
  Identifier   "Monitor2"
  VendorName   "Monitor Vendor"
  ModelName    "Monitor Model"
EndSection

Section "Device"
  Option      "RandRRotation" "on"
  Option      "Rotate" "right"
  Identifier  "Card0"
  BusID       "PCI:1:0:0"
  Driver      "nvidia"
  Option      "NoLogo" "True"
EndSection

Section "Device"
  Identifier  "Card1"
  BusID       "PCI:0:2:0"
  Driver      "intel"
  Option      "NoLogo" "True"
EndSection

Section "Device"
  Option      "RandRRotation" "on"
  Option      "Rotate" "left"
  Identifier  "Card2"
  BusID       "PCI:1:0:0"
  Driver      "nvidia"
  Option      "NoLogo" "True"
EndSection

Section "Screen"
  Identifier "Screen0"
  Device     "Card0"
  Monitor    "Monitor0"
  DefaultDepth 24
  SubSection "Display"
    Viewport   0 0
    Depth     16
  EndSubSection
  SubSection "Display"
    Viewport   0 0
    Depth     24
  EndSubSection
EndSection

Section "Screen"
  Identifier "Screen1"
  Device     "Card1"
  Monitor    "Monitor1"
  SubSection "Display"
    Viewport   0 0
    Depth     16
  EndSubSection
  SubSection "Display"
    Viewport   0 0
    Depth     24
  EndSubSection
EndSection

Section "Screen"
  Identifier "Screen2"
  Device     "Card2"
  Monitor    "Monitor2"
  SubSection "Display"
    Viewport   0 0
    Depth     16
  EndSubSection
  SubSection "Display"
    Viewport   0 0
    Depth     24
  EndSubSection
EndSection

Section "Module"
  Load  "glx"
  Load  "extmod"
  Load  "record"
  Load  "dbe"
EndSection

Section "InputDevice"
  Identifier  "Keyboard0"
  Driver      "kbd"
EndSection

Section "InputDevice"
  Identifier  "Mouse0"
  Driver      "mouse"
  Option      "Protocol" "auto"
  Option      "Device" "/dev/input/mice"
  Option      "ZAxisMapping" "4 5 6 7"
EndSection

Section "ServerLayout"
  Identifier   "X.org Configured"
  Screen       0 "Screen0" RightOf "Screen1"
  Screen       1 "Screen1" 0 0
  Screen       2 "Screen2" RightOf "Screen0"
  InputDevice  "Mouse0" "CorePointer"
  InputDevice  "Keyboard0" "CoreKeyboard"
  Option "Xinerama" "on"
EndSection

```

---

### Post by r_avital on 2013-09-05
Not sure you'll like this, but here's a few ideas,

I used to use Option "Rotate" "CCW" (or "left") like you.  The problem with that is, that every time I installed anything at all in Synaptic, I would watch the terminal window, and always see repeated messages "randr extension not available" or language to that effect.  For years, it had zero effect on the proper functioning of the machine.  But it basically nullifies the RandRRotation directive, and the reason I know that is, that under my nVidia settings application, the rotation option was missing. As soon as I take out the "Rotate" option, or comment it out (and KEEP the RandRRotation option), and reboot, the nVidia settings app shows me the rotation options. Sure, my screen was portrait (vertical) from login to logout, so who cares, right?  Until I decided I wanted the flexibility of rotating my screen at will for watching certain videos.

My solution was:

Edit the /etc/gdm/Init/Default script, to add the following at the very end, BEFORE the "exit 0" line:```
xrandr -o left
```
This will take care of rotating your login screen.  For rotating the actual desktop, you could write a script that does the same thing (just the same xrandr command as above) and launch it from startup-applications.

**The point is, **and this is where I think it could help, that xrandr **accepts a display number** (such as :0, :1, :2, etc.) on the command line, so you can have your script rotate each screen as you wish.  Something like:```
xrandr -d :0 -o left
xrandr -d :1 -o right
xrandr -d :2 -o normal
```
You get the idea.

See xrandr --help for more details, and I'm sure there's a man page for it as well.

HTH

---

