---
title: "Can't configure monitors with xrandr, leads to X crashing after waking from sleep"
date: 2019-01-18
forum: Hardware
---

### Post by sparr on 2019-01-18
First I encountered various problems trying to use xrandr to set up external monitors after they had successfully configured then disconnected and reconnected, possibly after the laptop was put to sleep in between. In those cases, every attempt to use xrandr, even `--auto` resulted in `xrandr: Configure crtc 1 failed`. I mention this because I suspect it is related to the bigger problem... 

Later I put my laptop to sleep then woke it up and got just a black screen. I hit ctrl+alt+f5 and the virtual terminal was working fine so then I hit ctrl+alt+f2 to go back to the default GUI and saw just a white underscore cursor in the top left corner. ctrl+alt+f1 brought me to the alternate GUI which started up just fine and presented a GUI login prompt. ctrl+alt+f2 then took me to a text tty2 which I did not expect.

Here are what I think are some key log entries:

dmesg:
```
[drm:intel_display_resume [i915]] *ERROR* Restoring old state failed with -22

```

Xorg.0.log:
```
[  2439.364] (II) event3  - Power Button: device removed
[  2439.400] (II) event5  - Video Bus: device removed
[  2439.424] (II) event1  - Power Button: device removed
[  2439.440] (II) event2  - Sleep Button: device removed
[  2439.456] (II) event7  - Integrated Webcam_HD: Integrate: device removed
[  2439.488] (II) event8  - DELL081C:00 044E:121F Mouse: device removed
[  2439.521] (II) event10 - DELL081C:00 044E:121F Touchpad: device removed
[  2439.552] (II) event11 - DELL081C:00 044E:121F UNKNOWN: device removed
[  2439.576] (II) event9  - Intel HID events: device removed
[  2439.600] (II) event6  - Dell WMI hotkeys: device removed
[  2439.616] (II) event4  - AT Translated Set 2 keyboard: device removed
[  2439.632] (II) AIGLX: Suspending AIGLX clients for VT switch
[  2447.245] (II) AIGLX: Resuming AIGLX clients after VT switch
[  2448.382] (EE) modeset(0): failed to set mode: No such file or directory
[  2448.382] (EE) 
Fatal server error:
[  2448.382] (EE) EnterVT failed for screen 0
[  2448.382] (EE) 
[  2448.382] (EE) 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[  2448.382] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[  2448.382] (EE) 
[  2448.382] (II) AIGLX: Suspending AIGLX clients for VT switch
[  2449.545] (EE) Server terminated with error (1). Closing log file.

```

I don't know how to proceed with further troubleshooting from here.

---

