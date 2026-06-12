---
title: "i8042 - Asus X450LN (R409) - touchpad is missing after suspend"
date: 2014-10-25
forum: Hardware
---

### Post by damagedspline on 2014-10-25
When I bought the laptop and first installed Ubuntu (14.04) the touchpad was not detected and installing the latest BIOS update (208) fixed this issue.
Now it detects and works fine at least until I do a suspend to RAM. When the laptop resumes from the suspend the touchpad is no longer detected.

Issue reproduce on both 14.04 & 14.10.

xinput before suspend:
```
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                  id=13   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                              id=9    [slave  keyboard (3)]
    &#8627; USB2.0 HD UVC WebCam                      id=10   [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                          id=11   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=12   [slave  keyboard (3)]

```

xinput after resume:
```
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                              id=9    [slave  keyboard (3)]
    &#8627; USB2.0 HD UVC WebCam                      id=10   [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                          id=11   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=12   [slave  keyboard (3)]

```

Even the sys is different - before suspend:
```
~/Downloads$ ls /sys/devices/platform/i8042/serio1/
bind_mode    drvctl       modalias     rate    reg_20  reg_24      resolution
debug        firmware_id  paritycheck  reg_07  reg_21  reg_25      resync_time
description  id           power        reg_10  reg_22  reg_26      subsystem
driver       input        protocol     reg_11  reg_23  resetafter  uevent
``` 

sys after resume:
```
ls /sys/devices/platform/i8042/serio1/
bind_mode description drvctl firmware_id id modalias power subsystem uevent

```

I have tried several combinations of the i8042 boot options but with no luck (nomux, noloop, etc...). 
Any ideas?

---

### Post by solo2 on 2015-02-19
I Had same problem with Asus x501u....
saw this somewhere, so not taking credit if it works...
"There's a nice graphical tool that alows you to simply enable and disable the touchpad. 
You can install it by typing on a console:



sudo add-apt-repository ppa:atareao/atareao

sudo apt-get update

sudo apt-get install touchpad-indicator



   
 
You can try to enable it from the System Settings

 
   
You can try running from the console synclient TouchpadOff=0
        

sudo gedit /etc/rc.local Before the line exit 0 you will add the following lines

:

sudo modprobe -r psmouse

sudo modprobe psmouse proto=imps

Save the file and reboot the computer"

---

