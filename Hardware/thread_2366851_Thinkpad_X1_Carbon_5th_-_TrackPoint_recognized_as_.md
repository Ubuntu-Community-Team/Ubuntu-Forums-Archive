---
title: "Thinkpad X1 Carbon 5th - TrackPoint recognized as ImPS/2 Generic Wheel Mouse"
date: 2017-07-22
forum: Hardware
---

### Post by procrastinator on 2017-07-22
On my Thinkpad X1 Carbon 5th gen TrackPoint recognized as ImPS/2 Generic Wheel Mouse, which makes it impossible to configure its sensitivity and speed (normally done at /devices/platform/i8042/serio1/serio2/sensitivity)

Seems like others have the [same]("http://www.spinics.net/lists/linux-input/msg51419.html") and [similar]("https://askubuntu.com/questions/924492/trackpoint-device-not-available-on-lenovo-carbon-x1-5th-generation") [problems]("https://unix.stackexchange.com/questions/359307/touchpad-recognied-as-imps-2-generic-wheel-mouse"). 
```

$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=11	[slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse              	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Integrated Camera                       	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                  	id=13	[slave  keyboard (3)]

```


```

$ dmesg | grep i8042
[    1.865376] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    3.506607] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[    5.436179] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/serio2/input/input7

```
```

$ ls /sys/devices/platform/i8042/serio1/serio2/sensitivity
ls: cannot access '/sys/devices/platform/i8042/serio1/serio2/sensitivity': No such file or directory

```

```

udevadm info -a -p /devices/platform/i8042/serio1/serio2/input/input7

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/platform/i8042/serio1/serio2/input/input7':
    KERNEL=="input7"
    SUBSYSTEM=="input"
    DRIVER==""
    ATTR{name}=="ImPS/2 Generic Wheel Mouse"
    ATTR{phys}=="synaptics-pt/serio0/input0"
    ATTR{properties}=="1"
    ATTR{uniq}==""

  looking at parent device '/devices/platform/i8042/serio1/serio2':
    KERNELS=="serio2"
    SUBSYSTEMS=="serio"
    DRIVERS=="psmouse"
    ATTRS{bind_mode}=="auto"
    ATTRS{description}=="Synaptics pass-through"
    ATTRS{firmware_id}==""
    ATTRS{protocol}=="ImPS/2"
    ATTRS{rate}=="100"
    ATTRS{resetafter}=="5"
    ATTRS{resolution}=="200"
    ATTRS{resync_time}=="0"

  looking at parent device '/devices/platform/i8042/serio1':
    KERNELS=="serio1"
    SUBSYSTEMS=="serio"
    DRIVERS=="psmouse"
    ATTRS{bind_mode}=="auto"
    ATTRS{description}=="i8042 AUX port"
    ATTRS{firmware_id}=="PNP: LEN0072 PNP0f13"
    ATTRS{protocol}=="SynPS/2"
    ATTRS{rate}=="80"
    ATTRS{resetafter}=="5"
    ATTRS{resolution}=="200"
    ATTRS{resync_time}=="0"

  looking at parent device '/devices/platform/i8042':
    KERNELS=="i8042"
    SUBSYSTEMS=="platform"
    DRIVERS=="i8042"
    ATTRS{driver_override}=="(null)"

  looking at parent device '/devices/platform':
    KERNELS=="platform"
    SUBSYSTEMS==""
    DRIVERS==""

```

---

### Post by efflandt on 2017-07-23
If you want to set sensitivity for that device only you can do it with xinput:```
xinput --set-ptr-feedback device threshold num denom
```For example ****```
xinput --set-ptr-feedback 12 5 2 1
```would set device id=**12** to move **5** pixels before it accelerates, then accelerate at the rate of **2** divided by **1**. The default acceleration changed from 2 to 5 with 16.04, which may work fine for a mousepad, but is too fast for a mouse or maybe your TrackPoint.

Once you find something that works, with Dash icon in upper left (if using Unity) "Search your computer" for "startup applications" and add a startup app to run the xinput command you want.

---

### Post by procrastinator on 2017-07-27
Tried your xinput suggestion with random values from 0.1 to 1000. It made no difference, unfortunately.

---

### Post by alphachaser on 2017-08-08
Has anyone been able to successfully modify the speed/sensitivity of the trackpoint? I'm still struggling, any help is appreciated, thanks.

---

