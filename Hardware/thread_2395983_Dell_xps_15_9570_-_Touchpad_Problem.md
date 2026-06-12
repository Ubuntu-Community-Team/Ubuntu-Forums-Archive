---
title: "Dell xps 15 9570 - Touchpad Problem"
date: 2018-07-09
forum: Hardware
---

### Post by pmartu12 on 2018-07-09
[COLOR=#101010][FONT=Ubuntu]Hello Guys,[/FONT][/COLOR]

[COLOR=#101010][FONT=Ubuntu]I have a dell xps 15 9570 with ubuntu 18.04 . It works fine but the only problem is the touchpad that is not detected.[/FONT][/COLOR]

[COLOR=#101010][FONT=Ubuntu]This is the output xinput:[/FONT][/COLOR]

[COLOR=#101010][FONT=Ubuntu]Virtual core pointer id=2 [master pointer (3)][/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]&#9116; &#8627; Virtual core XTEST pointer id=4 [slave pointer (2)][/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]&#9116; &#8627; USB Optical Mouse id=12 [slave pointer (2)][/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]&#9116; &#8627; Wacom HID 488E Pen stylus id=13 [slave pointer (2)][/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]&#9116; &#8627; Wacom HID 488E Finger touch id=14 [slave pointer (2)][/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]&#9116; &#8627; SynPS/2 Synaptics TouchPad id=19 [slave pointer (2)][/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]&#9116; &#8627; Wacom HID 488E Pen eraser id=20 [slave pointer (2)][/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]&#9123; Virtual core keyboard id=3 [master keyboard (2)][/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]&#8627; Virtual core XTEST keyboard id=5 [slave keyboard (3)][/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]&#8627; Power Button id=6 [slave keyboard (3)][/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]&#8627; Video Bus id=7 [slave keyboard (3)][/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]&#8627; Video Bus id=8 [slave keyboard (3)][/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]&#8627; Power Button id=9 [slave keyboard (3)][/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]&#8627; Sleep Button id=10 [slave keyboard (3)][/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]&#8627; Integrated_Webcam_HD: Integrate id=11 [slave keyboard (3)][/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]&#8627; Intel HID events id=15 [slave keyboard (3)][/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]&#8627; Intel HID 5 button array id=16 [slave keyboard (3)][/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]&#8627; Dell WMI hotkeys id=17 [slave keyboard (3)][/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]&#8627; AT Translated Set 2 keyboard id=18 [slave keyboard (3)][/FONT][/COLOR]

[COLOR=#101010][FONT=Ubuntu]I have also tried to set acpi=force and using JackHack96 image, but always the same problem.[/FONT][/COLOR]

[COLOR=#101010][FONT=Ubuntu]Has anyone solved this issue?[/FONT][/COLOR]

[COLOR=#101010][FONT=Ubuntu]Regards[/FONT][/COLOR]

---

### Post by vanadium on 2018-07-09
Is this a fresh installation? A touchpad is seen ( &#9116; &#8627; SynPS/2 Synaptics TouchPad id=19 [slave pointer (2)]) but apparently, it is not working. By default on a fresh linux 18.04, you would be using libinput drivers. The older generation of drivers is synaptics. To tell which driver you use, you can issue the commands "dpkg -l | grep synaptics" and "dpkg -l | grep libinput". No output means the driver is not installed.

Are you using Wayland or X-org? The command "echo $XDG_SESSION_TYPE" will tell you which display server you are running. By default on a fresh installation of Ubuntu 18.04, you will be using xorg.

---

### Post by pmartu12 on 2018-07-09
Yes I'm using xorg libinput. This is the output: 

dpkg -l | grep libinput
ii  libinput-bin                               1.10.4-1                            amd64        input device management and event handling library - udev quirks
ii  libinput10:amd64                           1.10.4-1                            amd64        input device management and event handling library - shared library
ii  xserver-xorg-input-libinput                0.27.1-1                            amd64        X.Org X server -- libinput input driver

I should see two touch pad like you can see in this guide [URL="https://www.dell.com/support/article/uk/en/ukdhs1/sln308258/precision-xps-ubuntu-general-touchpad-mouse-issue-fix?lang=en"]https://www.dell.com/support/article/uk/en/ukdhs1/sln308258/precision-xps-ubuntu-general-touchpad-mouse-issue-fix?lang=en. 
[/URL]I have also tried the guide above but nothing.

---

### Post by vanadium on 2018-07-09
You could try switching to the synaptics driver with the command "sudo apt install xserver-xorg-input-synaptics". You can remove this to revert. Is this a fresh install or an upgrade? Does the touchpad work in a live session, i.e. a session loaded from an install CD or USB?

---

### Post by pmartu12 on 2018-07-10
I have tried but always the same problem. Into live session from USB, the same problem. If I enter into UEFI bios, the touchpad works correctly.

---

### Post by gregory7 on 2018-07-14
I have exactly the same problem with a xiaomi laptop the touchpad works in the bios but doesn't work in either a live boot or the usual xorg gnome boot - very strange.

---

