---
title: "Ubuntu 13.10 with Lenovo Ideapad Flex 15 - no touchad detected"
date: 2014-01-26
forum: Hardware
---

### Post by I.Bun.Tu on 2014-01-26
I've purchased a Lenovo Ideapad Flex 15 after installing Ubuntu 13.10 (also tried Ubuntu 12.04.3 LTS) the touchpad works, but is not detected as a touchpad. I am pretty sure it is detected as a PS/2 mouse. The laptop house a touch screen as well as a touchpad. In my System Settings > Mouse & Touchpad section there are only 3 options: to change the primary button from left to right and to adjust the double click speed and pointer speed. There are no options for the touchpad (most importantly disable while typing). There is also no scrolling with the touchpad, either at the edges or with multi-touch and no other multi-touch features are active.

I was trying to seek help through askubuntu, but didn't get any response after the first day: [http://askubuntu.com/questions/398568/ubuntu-13-10-touchpad-drivers-not-working-synaptics-not-loaded-lenovo-ideapad](http://askubuntu.com/questions/398568/ubuntu-13-10-touchpad-drivers-not-working-synaptics-not-loaded-lenovo-ideapad)

The question details some of the steps I've taken to try and fix the problem. Mostly what I have found in trying to troubleshoot the issue is people have fixed the problem by applying a patch containing the drivers for their touchpad (because they were either not apart of the current kernel or became corrupted in some way) which was later comitted to the kernel. I have tried all of the latest patches suggested for this problem but they do not provide me any solution.

Here is some system info, please let me know if I can provide more information or how I should go about troubleshooting this issue:

```
freedom@flex15:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                          id=12    [slave  pointer  (2)]
&#9116;   &#8627; eGalax Inc. eGalaxTouch EXC7910-1026-13.00.00    id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Lenovo EasyCamera                           id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; Ideapad extra buttons                       id=13    [slave  keyboard (3)]
```

```
freedom@flex15:~$ dmesg | grep -i touch
[    1.393141] usb 2-1: Product: eGalaxTouch EXC7910-1026-13.00.00
[    3.305584] input: eGalax Inc. eGalaxTouch EXC7910-1026-13.00.00 as /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.0/input/input5
[    3.315145] hid-multitouch 0003:0EEF:A111.0001: input,hiddev0,hidraw0: USB HID v2.10 Device [eGalax Inc. eGalaxTouch EXC7910-1026-13.00.00] on usb-0000:00:14.0-1/input0
[    3.534215] psmouse serio1: alps: Unknown ALPS touchpad: E7=73 03 0a, EC=88 b6 06
[ 3451.666414] psmouse serio1: alps: Unknown ALPS touchpad: E7=73 03 0a, EC=88 b6 06
[ 3453.901185] usb 2-1: Product: eGalaxTouch EXC7910-1026-13.00.00
[ 3453.902731] input: eGalax Inc. eGalaxTouch EXC7910-1026-13.00.00 as /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.0/input/input14
[ 3453.902983] hid-multitouch 0003:0EEF:A111.0002: input,hiddev0,hidraw0: USB HID v2.10 Device [eGalax Inc. eGalaxTouch EXC7910-1026-13.00.00] on usb-0000:00:14.0-1/input0
[ 6533.261219] psmouse serio1: alps: Unknown ALPS touchpad: E7=73 03 0a, EC=88 b6 06
[ 6535.482613] usb 2-1: Product: eGalaxTouch EXC7910-1026-13.00.00
[ 6535.484335] input: eGalax Inc. eGalaxTouch EXC7910-1026-13.00.00 as /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.0/input/input15
[ 6535.484530] hid-multitouch 0003:0EEF:A111.0003: input,hiddev0,hidraw0: USB HID v2.10 Device [eGalax Inc. eGalaxTouch EXC7910-1026-13.00.00] on usb-0000:00:14.0-1/input0

```

```
freedom@flex15:~$ synclient -l
Couldn't find synaptics properties. No synaptics driver loaded?

```

And 'sudo modprobe psmouse' returns nothing.

Please help, I've been putting up with this for close to a month but I can hardly stand it anymore. I can't scroll and almost every time I type, the touchpad clicks off of what I'm typing. I really need to get my touchpad detected. Thank you.

---

