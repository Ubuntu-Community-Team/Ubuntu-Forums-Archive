---
title: "Touchpad vertical scrolling stopped working"
date: 2008-11-21
forum: Hardware
---

### Post by muadnu on 2008-11-21
I already asked about this in another [thread]("http://ubuntuforums.org/showthread.php?t=271052") about a different issue but got no answers, so I'm starting a new one.

After installing Intrepid I couldn't get syndaemon to work for my touchpad (syndaemon is a little utility to disable a synaptics touchpad temporarily while you type). I followed all instructions but it didn't work. Up to this point vertical scrolling worked perfectly for my touchpad. I finally got syndaemon working by using the binary provided [here]("http://people.ubuntuwire.com/~fujitsu/syndaemon") instead of the one coming in Intrepid. 

Now vertical scrolling doesn't work. I doubt it has to do with the binary I'm using (it actually doesn't work if I kill it either), and I'm guessing the issue is with some configuration I changed, but I just cannot get it right.

Below is the relevant part of my xorg.conf file. At this point I don't know how relevant it is, since seemingly now these things are handled through other configuration files. I do know that some settings are read here (like accelfactor, and min and max speed). But, for instance, I'm not sure my "Option SHMConfig = on" line is making any difference.

```

```
Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
    Option         "SHMConfig" "on"
    Option         "MinSpeed" "0.60"
    Option         "MaxSpeed" "1.50" # 1.1
    Option         "AccelFactor" "0.10" # 0.07
    Option         "EdgeMotionMinSpeed" "200"
    Option         "EdgeMotionMaxSpeed" "200"
    Option         "UpDownScrolling" "1"
EndSection

---

### Post by muadnu on 2008-11-29
I still haven't found a solution... Does anyone have any idea?

---

