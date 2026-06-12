---
title: "Disable touchpad when mouse plugged in."
date: 2014-09-22
forum: Hardware
---

### Post by Tadaen_Sylvermane on 2014-09-22
This feature is built into Kubuntu. No such luck for others though. I started with [http://ubuntuforums.org/showthread.php?t=2174740](http://ubuntuforums.org/showthread.php?t=2174740) . I modified to this...

```
#!/bin/bash

##### begin script #####


tpad_toggle() {
# mouse lsusb identifier
    MYMOUSE="Logitech, Inc. Unifying Receiver"
# set variable of touchpad mode
    TPSTATE=$(synclient -l | grep TouchpadOff | awk '{ print $3 }')
# detect if mouse plugged in
    if lsusb | grep "$MYMOUSE" ; then
        if [[ "$TPSTATE" != 1 ]] ; then
            synclient touchpadoff=1
        fi
    else
        if [[ "$TPSTATE" == 1 ]] ; then
            synclient touchpadoff=2
        fi
    fi
}


while true
do
    tpad_toggle
    sleep 10
done


##### end script #####

```

It works fine, runs every 10 seconds to check if my mouse is plugged in, if so then it disables the touchpad if it's enabled. Simple really. However when the mouse is removed and it reactivates the touchpad the tap to click and 2 finger drag doesn't work. The buttons on the touchpad itself work but the tap in the touchpad field isn't working. Or is this an entire waste of time and is there a app I can add to gnomeshell to do this?

---

