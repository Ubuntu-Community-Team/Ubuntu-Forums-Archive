---
title: "Touchpad not working anymore after an update"
date: 2014-01-03
forum: Hardware
---

### Post by levasseur-cl on 2014-01-03
Hi,

Until yesterday, my touchpad worked correctly, but after an update, it didn't work anymore. `xinput list` doesn't even list it. I'm using Ubuntu 13.10 with kernel 3.11.0-15 on a HP Chromebook 14 (not the pavillon, the model with the haswell cpu). I don't know exactly what I could do to reenable it. I searched for a shortcut that would enable/disable it, but I didn't find anything. I also tried to run 

```
sudo modprobe -r psmouse
sudo modprobe psmouse proto=imps
```

but it didn't work.

Here is xinput list result:

```

$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech Unifying Device. Wireless PID:1025    id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=10    [slave  keyboard (3)]
    &#8627; HP Truevision HD                            id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]


```

The logitech is a mouse, which fortunately is working.

Is there a way to get it working again ?

---

### Post by varunendra on 2014-01-04
Welcome to Ubuntu Forums levasseur-cl !

Do we have any clues in syslog or Xorg.0.log? Please post the outputs of (soon after a fresh boot) -
```
grep -i touchpad /var/log/syslog
grep -i touchpad /var/log/Xorg.0.log
```

Also, is it also missing from **/proc/bus/input/devices** file? The output of -
```
cat /proc/bus/input/devices
```

---

### Post by levasseur-cl on 2014-01-04
Thanks for your help, I tried your command, there is no log about the touchpad and I think it is also missing from **/proc/bus/input/devices** file.

```
$ grep -i touchpad /var/log/syslog
$ grep -i touchpad /var/log/Xorg.0.log
$ cat /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
U: Uniq=
H: Handlers=event0 
B: PROP=0
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: PROP=0
B: EV=3
B: KEY=4000 0 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0E:01/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: PROP=0
B: EV=3
B: KEY=4000 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0011 Vendor=0001 Product=0001 Version=ab83
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input5
U: Uniq=
H: Handlers=sysrq kbd event5 
B: PROP=0
B: EV=120013
B: KEY=20000 20 0 0 1500f02100000 3803078f900d401 feffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0

I: Bus=0003 Vendor=04f2 Product=b40d Version=1826
N: Name="HP Truevision HD"
P: Phys=usb-0000:00:14.0-3/button
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb2/2-3/2-3:1.0/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel MID HDMI/DP,pcm=8"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:03.0/sound/card0/input8
U: Uniq=
H: Handlers=event8 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel MID HDMI/DP,pcm=7"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:03.0/sound/card0/input9
U: Uniq=
H: Handlers=event9 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel MID HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:03.0/sound/card0/input10
U: Uniq=
H: Handlers=event10 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card1/input11
U: Uniq=
H: Handlers=event11 
B: PROP=0
B: EV=21
B: SW=4

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Mic"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card1/input12
U: Uniq=
H: Handlers=event12 
B: PROP=0
B: EV=21
B: SW=10

I: Bus=0003 Vendor=046d Product=c52b Version=0111
N: Name="Logitech Unifying Device. Wireless PID:1025"
P: Phys=usb-0000:00:14.0-8:1
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb2/2-8/2-8:1.2/0003:046D:C52B.0003/input/input13
U: Uniq=
H: Handlers=mouse0 event13 
B: PROP=0
B: EV=17
B: KEY=ffff0000 0 0 0 0
B: REL=143
B: MSC=10


```

---

### Post by varunendra on 2014-01-04
Make sure the touchpad is enabled in BIOS, and if it is still missing in the logs and **xinput** outputs (and the shortcut-key/switch, if any, to turn it on/off has no effect), I think it is time to submit a bug report at launchpad against the kernel. Please see this wiki page : [https://wiki.ubuntu.com/DebuggingTouchpadDetection](https://wiki.ubuntu.com/DebuggingTouchpadDetection)

---

### Post by levasseur-cl on 2014-01-05
Thanks, I've just reported a bug at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1266186](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1266186)

---

### Post by varunendra on 2014-01-05
Nice job !

I suggest looking around on this and other forums and if you see others having same issue, encourage them to add themselves to the 'Affected' list of your bug report. Since this seems to be a bug in the kernel itself, I believe other Linux distros should be affected too. You may test a few live ones to check that yourself, and update the report accordingly.

---

### Post by levasseur-cl on 2014-01-06
Actually, I'm not sure that the problem is related to the kernel. I tried previous kernel versions (3.11.0-[12,13,14,15]-generic) and my touchpad doesn't work with any of them. Unfortunately I don't remember what was the version of the kernel I used when it still worked. Maybe my former kernel was older than those I tried, but I can't find a kernel older than 3.11.0-12-generic in my repo, is there another repo where I could find other versions ? Maybe more recent version could work too

---

### Post by varunendra on 2014-01-07
You can manually download .dep packages of older, as well as latest kernels from kernel ppa mainline : [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

It is recommended to also download and install (by simply double-clicking) the headers of the same version whose kernel (linux-image...) you choose to install. It is needed when compiling source of packages/drivers.

---

### Post by levasseur-cl on 2014-01-07
This script fixes the bug, at least for this laptop:
[https://googledrive.com/host/0B0YvUuHHn3MndlNDbXhPRlB2eFE/cros-haswell-modules.sh](https://googledrive.com/host/0B0YvUuHHn3MndlNDbXhPRlB2eFE/cros-haswell-modules.sh)

---

### Post by varunendra on 2014-01-08
Awesome !

Since the script seems to be applying a few online patches directly to the kernel, I'd say definitely a bug. Hopefully the patches would be already applied in newer kernels so the patching won't be needed.

For others who might come across this thread - the script seems to be meant for Chromebook only. Although it also rebuilds some "i2c-xx" drivers whose role I'm not sure about, so can't say for sure if it would be applicable to other platforms or not.

---

