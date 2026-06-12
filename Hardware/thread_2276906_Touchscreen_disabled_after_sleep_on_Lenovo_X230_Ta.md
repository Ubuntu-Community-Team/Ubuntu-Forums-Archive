---
title: "Touchscreen disabled after sleep on Lenovo X230 Tablet (X230t)"
date: 2015-05-05
forum: Hardware
---

### Post by kyrachris on 2015-05-05
I recently upgraded UbuntuGnome to 15.04, and now when the laptop sleeps, after wakeup Ubuntu no longer recognizes/uses the touchscreen. In the Wacom settings menu, it says "No tablet detected". I didn't have any issues prior, so it appears to be something that changed or some settings that were overwritten as part of the upgrade. Have any other X230t users experienced this issue? Are there any work-arounds?

```
$ lsusb
Bus 004 Device 003: ID 056a:00e6 Wacom Co., Ltd 
Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 004: ID 04f2:b2ea Chicony Electronics Co., Ltd Integrated Camera [ThinkPad]
Bus 003 Device 003: ID 147e:2020 Upek TouchChip Fingerprint Coprocessor (WBF advanced mode)
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

$ xinput -list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                       id=16    [slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 E6 Pen eraser                   id=15    [slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 E6 Finger touch                 id=11    [slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 E6 Pen stylus                   id=10    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; Integrated Camera                           id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                      id=14    [slave  keyboard (3)]

$ xsetwacom --list devices
Wacom ISDv4 E6 Pen eraser           id: 15    type: ERASER    
Wacom ISDv4 E6 Finger touch         id: 11    type: TOUCH     
Wacom ISDv4 E6 Pen stylus           id: 10    type: STYLUS    

```

---

### Post by kyrachris on 2015-05-09
I figured out a fix by combining elements from these two sources:

[http://ubuntuforums.org/showthread.php?t=2244342&highlight=touchscreen+disabled+sleep](http://ubuntuforums.org/showthread.php?t=2244342&highlight=touchscreen+disabled+sleep) Comment #3
[http://forums.fedoraforum.org/showthread.php?t=299457](http://forums.fedoraforum.org/showthread.php?t=299457) Comment #3

Here's what I did:

```
cd /lib/systemd/system-sleep/
sudo nano wacom
```

Type the following:

```
#!/bin/bash
case "${1}" in
  resume|thaw|post)
         rmmod usbhid
         modprobe usbhid
         ;;
     *)
         ;;
esac
exit $?
```

Save and exit (CTRL+S, CTRL+X). Then mark as executable:

```
sudo chmod +x wacom
```

Test by sleeping and resuming. This script works in this location because PM-UTILs is not used to put the computer to sleep any more. SYSTEMD does this, and it uses a different directory for sleep/resume scripts.

---

