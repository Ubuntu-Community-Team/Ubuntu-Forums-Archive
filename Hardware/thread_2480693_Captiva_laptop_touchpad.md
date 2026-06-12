---
title: "Captiva laptop touchpad"
date: 2022-11-06
forum: Hardware
---

### Post by _FB_ on 2022-11-06
Hello Everybody.
I recently bought a laptop from a company that is not mainstream.  It's a Captiva I68-189, a German brand if I understand well.
The good thing is that they come without OS, so I installed Ubuntu.  Everything seemed smooth at the beginning but then I started to have some problems
with the touchpad.  After a while the touchpad stop working.  I am unsure about what to do, I googled a lot and I tried some solutions but nothing worked for me.
Currently, I am also using a wireless mouse (I tried to unplug it when I have the problem, but with no effect).
I wonder if some people could help me in diagnose and solve this problem.

```
xinput --list&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=10    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver Consumer Control      id=11    [slave  pointer  (2)]
&#9116;   &#8627; FTCS1000:01 2808:0102 Mouse                 id=13    [slave  pointer  (2)]
&#9116;   &#8627; FTCS1000:01 2808:0102 Touchpad              id=14    [slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse                  id=17    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; BisonCam,NB Pro: BisonCam,NB Pr             id=12    [slave  keyboard (3)]
    &#8627; Intel HID events                            id=15    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=16    [slave  keyboard (3)]
    &#8627; Logitech USB Receiver Consumer Control      id=18    [slave  keyboard (3)]

```


```
 cat /proc/bus/input/devices
I: Bus=0018 Vendor=2808 Product=0102 Version=0100N: Name="FTCS1000:01 2808:0102 Touchpad"
P: Phys=i2c-FTCS1000:01
S: Sysfs=/devices/pci0000:00/0000:00:15.0/i2c_designware.0/i2c-1/i2c-FTCS1000:01/0018:2808:0102.0001/input/input17
U: Uniq=
H: Handlers=mouse1 event11 
B: PROP=5
B: EV=1b
B: KEY=e520 10000 0 0 0 0
B: ABS=2e0800000000003
B: MSC=20

```

---

### Post by mIk3_08 on 2022-11-07
> **_FB_ said:**
> Hello Everybody.
I recently bought a laptop from a company that is not mainstream.  It's a Captiva I68-189, a German brand if I understand well.
The good thing is that they come without OS, so I installed Ubuntu.  Everything seemed smooth at the beginning but then I started to have some problems
with the touchpad.  After a while the touchpad stop working.  I am unsure about what to do, I googled a lot and I tried some solutions but nothing worked for me.
Currently, I am also using a wireless mouse (I tried to unplug it when I have the problem, but with no effect).
I wonder if some people could help me in diagnose and solve this problem.

```
 cat /proc/bus/input/devices
I: Bus=0018 Vendor=2808 Product=0102 Version=0100N: Name="FTCS1000:01 2808:0102 Touchpad"
P: Phys=i2c-FTCS1000:01
S: Sysfs=/devices/pci0000:00/0000:00:15.0/i2c_designware.0/i2c-1/i2c-FTCS1000:01/0018:2808:0102.0001/input/input17
U: Uniq=
H: Handlers=mouse1 event11 
B: PROP=5
B: EV=1b
B: KEY=e520 10000 0 0 0 0
B: ABS=2e0800000000003
B: MSC=20

```
Can you paste all the results of your "input/devices" it seems that I can't see any results of your wireless mouse as you mentioned above that you encounter some issue with it and even in your xinput results your wireless mouse was not present. It only says that PS/2 Generic Wheel Mouse . Thanks. Regards and cheers.

---

### Post by _FB_ on 2022-11-07
Thank you for your reply here the entire result:

```
cat /proc/bus/input/devicesI: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0


I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=4000 0 0


I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
U: Uniq=
H: Handlers=event2 
B: PROP=0
B: EV=21
B: SW=1


I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0


I: Bus=0011 Vendor=0001 Product=0001 Version=ab83
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input4
U: Uniq=
H: Handlers=sysrq kbd event4 leds 
B: PROP=0
B: EV=120013
B: KEY=402000000 3803078f800d001 feffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7


I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Intel HID events"
P: Phys=
S: Sysfs=/devices/platform/INTC1051:00/input/input10
U: Uniq=
H: Handlers=rfkill kbd event7 
B: PROP=0
B: EV=13
B: KEY=81000300000000 5000004000 1e294000000020 0
B: MSC=10


I: Bus=0003 Vendor=046d Product=c526 Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:14.0-7/input0
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0/0003:046D:C526.0002/input/input11
U: Uniq=
H: Handlers=mouse0 event5 
B: PROP=0
B: EV=17
B: KEY=ffff0000 0 0 0 0
B: REL=1943
B: MSC=10


I: Bus=0003 Vendor=046d Product=c526 Version=0111
N: Name="Logitech USB Receiver Consumer Control"
P: Phys=usb-0000:00:14.0-7/input1
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.1/0003:046D:C526.0003/input/input12
U: Uniq=
H: Handlers=kbd event6 
B: PROP=0
B: EV=1f
B: KEY=306ff 0 0 483ffff17aff32d bfd4444600000000 1 130ff38b17c000 677bfad9415fed 9ed68000004400 10000002
B: REL=1040
B: ABS=100000000
B: MSC=10


I: Bus=0003 Vendor=5986 Product=9102 Version=0601
N: Name="BisonCam,NB Pro: BisonCam,NB Pr"
P: Phys=usb-0000:00:14.0-8/button
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb3/3-8/3-8:1.0/input/input15
U: Uniq=
H: Handlers=kbd event8 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0


I: Bus=0018 Vendor=2808 Product=0102 Version=0100
N: Name="FTCS1000:01 2808:0102 Mouse"
P: Phys=i2c-FTCS1000:01
S: Sysfs=/devices/pci0000:00/0000:00:15.0/i2c_designware.0/i2c-1/i2c-FTCS1000:01/0018:2808:0102.0001/input/input16
U: Uniq=
H: Handlers=mouse1 event9 
B: PROP=0
B: EV=17
B: KEY=30000 0 0 0 0
B: REL=903
B: MSC=10


I: Bus=0018 Vendor=2808 Product=0102 Version=0100
N: Name="FTCS1000:01 2808:0102 Touchpad"
P: Phys=i2c-FTCS1000:01
S: Sysfs=/devices/pci0000:00/0000:00:15.0/i2c_designware.0/i2c-1/i2c-FTCS1000:01/0018:2808:0102.0001/input/input17
U: Uniq=
H: Handlers=mouse2 event10 
B: PROP=5
B: EV=1b
B: KEY=e520 10000 0 0 0 0
B: ABS=2e0800000000003
B: MSC=20


I: Bus=0011 Vendor=0002 Product=0005 Version=0000
N: Name="ImPS/2 Generic Wheel Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input6
U: Uniq=
H: Handlers=mouse3 event11 
B: PROP=1
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=103


I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input19
U: Uniq=
H: Handlers=kbd event12 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Mic"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1f.3/sound/card0/input20
U: Uniq=
H: Handlers=event13 
B: PROP=0
B: EV=21
B: SW=10


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Front Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1f.3/sound/card0/input21
U: Uniq=
H: Handlers=event14 
B: PROP=0
B: EV=21
B: SW=4


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1f.3/sound/card0/input22
U: Uniq=
H: Handlers=event15 
B: PROP=0
B: EV=21
B: SW=140


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=7"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1f.3/sound/card0/input23
U: Uniq=
H: Handlers=event16 
B: PROP=0
B: EV=21
B: SW=140


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=8"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1f.3/sound/card0/input24
U: Uniq=
H: Handlers=event17 
B: PROP=0
B: EV=21
B: SW=140


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=9"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1f.3/sound/card0/input25
U: Uniq=
H: Handlers=event18 
B: PROP=0
B: EV=21
B: SW=140


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=10"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1f.3/sound/card0/input26
U: Uniq=
H: Handlers=event19 
B: PROP=0
B: EV=21
B: SW=140


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=11"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1f.3/sound/card0/input27
U: Uniq=
H: Handlers=event20 
B: PROP=0
B: EV=21
B: SW=140


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=12"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1f.3/sound/card0/input28
U: Uniq=
H: Handlers=event21 
B: PROP=0
B: EV=21
B: SW=140


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=13"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1f.3/sound/card0/input29
U: Uniq=
H: Handlers=event22 
B: PROP=0
B: EV=21
B: SW=140


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=14"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1f.3/sound/card0/input30
U: Uniq=
H: Handlers=event23 
B: PROP=0
B: EV=21
B: SW=140


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=15"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1f.3/sound/card0/input31
U: Uniq=
H: Handlers=event24 
B: PROP=0
B: EV=21
B: SW=140


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=16"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1f.3/sound/card0/input32
U: Uniq=
H: Handlers=event25 
B: PROP=0
B: EV=21
B: SW=140


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=17"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1f.3/sound/card0/input33
U: Uniq=
H: Handlers=event26 
B: PROP=0
B: EV=21
B: SW=140



```

---

### Post by mIk3_08 on 2022-11-09
Maybe here is the answer of you question. [Click here]("https://unix.stackexchange.com/questions/5117/how-is-new-hardware-support-added-to-the-linux-kernel#5118"). Regards and cheers.

---

