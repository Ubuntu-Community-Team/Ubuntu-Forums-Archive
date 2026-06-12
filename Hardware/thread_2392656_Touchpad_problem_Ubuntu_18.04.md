---
title: "Touchpad problem Ubuntu 18.04"
date: 2018-05-23
forum: Hardware
---

### Post by voodoolovedog2 on 2018-05-23
It's been a long time since I've visited these boards. Most of the time I can find a solution to my problem without posting, however now I need a little help.

I'm trying to get Ubuntu 18.04 working on a Panasonic Toughbook CF-53. I'm almost at the finish line because almost every device worked right out of the gate. However, the touchscreen is not working at all. Poking around I dug up the information to resolve the issue but it seems that Ubuntu is confusing the input values between the touchpad and the touchscreen. 

xinput doesn't show the device at all:

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; USB2.0 Camera: USB2.0 Camera                id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]
    &#8627; Panasonic Laptop Support                    id=12    [slave  keyboard (3)]

dmesg told me that the hardware was found:

dmesg | grep -i touch

[    3.040149] usb 2-1.7: Product: USB Touch Panel
[    3.048964] input: Fujitsu Component USB Touch Panel as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.7/2-1.7:1.0/0003:0430:0532.0001/input/input11
[    3.049054] hid-generic 0003:0430:0532.0001: input,hidraw0: USB HID v1.11 Device [Fujitsu Component USB Touch Panel] on usb-0000:00:1d.0-1.7/input0
[    3.079167] psmouse serio2: synaptics: Touchpad model: 1, fw: 7.5, id: 0x1c0b1, caps: 0xd00033/0x244000/0xa0400/0x0, board id: 372, fw id: 813957
[    3.117695] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input9

and there's where it hit me. The touchpad is on input9 and the touchscreen is on input11. But xinput has assigned the touchpad input11, thus ignoring the touchscreen. 

Selective cat from /proc/bus/input/devices

I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio2/input0
S: Sysfs=/devices/platform/i8042/serio2/input/input9
U: Uniq=
H: Handlers=mouse1 event6 
B: PROP=9
B: EV=b
B: KEY=6420 3000f 0 0 0 0
B: ABS=260800011000003

I: Bus=0003 Vendor=0430 Product=0532 Version=0111
N: Name="Fujitsu Component USB Touch Panel"
P: Phys=usb-0000:00:1d.0-1.7/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.7/2-1.7:1.0/0003:0430:0532.0001/input/input11
U: Uniq=
H: Handlers=mouse0 event5 
B: PROP=0
B: EV=1b
B: KEY=c03 0 0 0 0 0
B: ABS=3
B: MSC=10

So how to I force Ubuntu (or xinput, I guess) to assign the touchpad to input9? Which I guess would then allow the touchscreen to take input11?

Thanks for your time.

---

### Post by voodoolovedog2 on 2018-06-04
Anyone?

---

### Post by monkeybrain20122 on 2018-06-04
Try

sudo apt install xserver-xorg-input-synaptics

and reboot.

---

### Post by bodhin2 on 2018-06-04
i asked this in response to another thread.  so are there still touchpad issues with ubuntu?  random jumping os cursor and also double clicking and openeing 100 windows accidentally?

---

### Post by kazakore on 2018-06-05
> **bodhin2 said:**
> i asked this in response to another thread.  so are there still touchpad issues with ubuntu?  random jumping os cursor and also double clicking and openeing 100 windows accidentally?

Despite the title of this thread I believe this is really more about a touchscreen issue than touchpad....

But to answer your question I believe there is some issues and it to an extent depends on the DE you use. Mostly Ubuntu seems to have migrated to libinput but Xubuntu doesn't work 100% correctly with this driver and comes with the synaptics one (or so I believe.) I run Studio, which should be based on Xubuntu but came with libinput and i was having weird issues (main one being scrolling upwards was very temperamental) so had to manually change it to use the synaptics one. Once I had done that I have absolutely zero issues (and generally haven't since I started with Ubuntu with 14.04)

Jumping mouse and extra clicks I read is usually caused by two drivers trying to control the same device. running xinput should give you an indication if this is the case for you.

Apologies to voodoolovedog2 for replying to the off topic conversation in your thread. Wish I could help you with your issue but I have no idea. bodhin2 please start your own thread if you wish to talk about such things more.

---

### Post by voodoolovedog2 on 2018-06-07
> **monkeybrain20122 said:**
> Try

sudo apt install xserver-xorg-input-synaptics

and reboot.

I eagerly ran this command and was very hopeful it would resolve my issue, but it doesn't. The OS still "sees" the touchpad as input11 even though it's listed in /proc/bus/input as input9. xinput still does not display the touchscreen. 

:(

---

### Post by booq on 2018-09-06
Hello, 

Is there a solution for this problem ? I experienced similar issue on a HP Zbook Studio G5.

---

### Post by serge-hallyn on 2018-10-24
Hi,

if it's anything like the touchscreen on my CF-19 (which the dmesg output suggests it is), what I had to do was to install xserver-xorg-input-evdev, and purge xserver-xorg-input-libinput.  (just installing evdev was not enough)

---

