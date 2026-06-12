---
title: "Mouse problems with only newer kernels."
date: 2012-12-05
forum: Hardware
---

### Post by moon_raker on 2012-12-05
Refers Kubuntu 12.04/12.10 as well as all newer live cd's (kernels 3.2x > 3.5x)

 I noticed that the entries in the menus of some apps can sometimes not be selected/highlighted - there is a hesitant flickering when passing over with the mouse, disabling effects does not help and also not a nvidia card issue as there are no problems with Scientific Linux on sdb.
 I also cannot use tty terminals (1>6) as my login is rejected (password invalid). Copy paste works on and off.
 Furthermore I also have this mouse problem with Live CD's using the newer kernels i.e. 3.2x and 3.5x.


 I have now found that the problems are due to the mouse. I know this because everything is fine with an old Logitech mouse I had stored at the back of my cupboard.
 The question now is what to do ?
 The problematic mouse is part of a Microsoft Wirelesss Comfort Desktop 5000 ( i.e. mouse and keyboard). It works off usb (Microsoft 2.4 GHz Transceiver v.6.0).
 Some kernel update may have caused the problem, as it is a new thing and I don't experience the symptoms mentioned in Scientific Linux 6.3 
 Here is what nvidia settings says, Kubuntu and Sc. Linux ......

```
**Kubuntu 12.04/12.10 >>**

       Section "InputDevice"
            # generated from default
            Identifier     "Mouse0"
            Driver         "mouse"
            Option         "Protocol" "auto"
            Option         "Device" "/dev/psaux"
            Option         "Emulate3Buttons" "no"
            Option         "ZAxisMapping" "4 5"
        EndSection

        Section "InputDevice"
            # generated from default
            Identifier     "Keyboard0"
            Driver         "kbd"
        EndSection

        **Scientific Linux 6.3 >>**  No problems.

        Section "InputDevice"

            # generated from default
        	Identifier  "Mouse0"
        	Driver      "mouse"
        	Option	    "Protocol" "auto"
        	Option	    "Device" "/dev/input/mice"
        	Option	    "Emulate3Buttons" "no"
        	Option	    "ZAxisMapping" "4 5"
        EndSection

        Section "InputDevice"

            # generated from data in "/etc/sysconfig/keyboard"
        	Identifier  "Keyboard0"
        	Driver      "kbd"
        	Option	    "XkbLayout" "us"
        	Option	    "XkbModel" "pc105"
        EndSection
```

Have tried changing a few lines in xorg.conf eg. replacing Option "device" "/dev/psaux" with "/dev/input/mice". No luck also with modprobe mousedev.

What can I do, short of buying a new mouse/keyboard ?:(

---

### Post by Rocky1937 on 2013-12-04
I also have the same basic problem after upgrade from K 12.10 to K13.10  Three different logitech wireless mice all have the same problem - a usb logitech mouse works fine.  Switching to X desktop the problem goes away.  My problem is affecting only left/right button selections BY NOT selecting my choice after a selection action.

---

### Post by mörgæs on 2013-12-04
Thanks for reporting. 
If the bug is still in 14.04 it would be good with a formal report in Launchpad.

---

