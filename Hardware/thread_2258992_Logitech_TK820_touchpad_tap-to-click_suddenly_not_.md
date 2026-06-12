---
title: "Logitech TK820 touchpad tap-to-click suddenly not working"
date: 2015-01-01
forum: Hardware
---

### Post by inertiaO on 2015-01-01
I have a TK820 keyboard which was working great then suddenly the touchpad tap to click functionality has completely stopped working. It has been working for months in that I could tap to simulate a mouse click or tap with two fingers to simulate a right mouse click. 

I tested the keyboard in Windows and that functionality works straight away so I know the keyboard is not broken.

I read about similar problems with an older pad that were fixed by updating the firmware, but this has not helped on my TK820. Is there some problem now with the Kernel? (I am using 3.16 Ubuntu 1410) or something to do with the synaptic configuration?

---

### Post by Tuxclear on 2015-01-01
Check System settings>Mouse & touchpad to see if the options have been disabled.

---

### Post by inertiaO on 2015-01-01
Everything is as it should be there.

The touchpad works just fine. I can use two fingers to page and down, for example. Previous searching said that the firmware in another Logitech unit didn't support the sending of the tap as mouse click event and was fixed in a firmware update so that the control of the click was OS independent. However, it's the fact it has worked just fine up until yesterday that is the problem. I have even reinstalled Ubuntu from scratch and it's still the same. There is nothing I can see on the keyboard that might have toggled the functionality off. I suspect Kernel or Xserver support but I cannot say which version of either I was using before.

---

### Post by Tuxclear on 2015-01-01
Can you give the output of 

[COLOR=#008000]cat /proc/bus/input/devices
[/COLOR]
[FONT=arial]and the contents of[/FONT]

*/etc/xorg.conf*  [FONT=arial]if there is anything[/FONT].

---

### Post by inertiaO on 2015-01-01
I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0003 Vendor=046d Product=c52b Version=0111
N: Name="Logitech Unifying Device. Wireless PID:4102"
P: Phys=usb-0000:00:12.0-3:1
S: Sysfs=/devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.2/0003:046D:C52B.0003/0003:046D:C52B.0004/input/input5
U: Uniq=
H: Handlers=sysrq kbd mouse0 event2 
B: PROP=0
B: EV=12001f
B: KEY=3007f 0 0 83ffff17aff32d bf54444600000000 ffff0001 130f978b17c007 ffff73fad941dfff febeffdfffefffff fffffffffffffffe
B: REL=1c3
B: ABS=100000000
B: MSC=10
B: LED=1f

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA ATI HDMI HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card0/input6
U: Uniq=
H: Handlers=event3 
B: PROP=0
B: EV=21
B: SW=140

---

### Post by ajgreeny on 2015-01-01
What does command ```
synclient -l | grep MaxTapTime
``` give you as output?

I don't know why, or if, it can be differently set in that and the GUI for system settings, but it is worth looking to see how synclient is set.

---

### Post by Tuxclear on 2015-01-01
Better run:
[FONT=arial][COLOR=#008000]
cat /proc/bus/input/devices > ~/devices[/COLOR][/FONT][FONT=arial narrow][FONT=book antiqua]

[/FONT][/FONT]and show the output.

---

### Post by inertiaO on 2015-01-01
Thanks for the help!

If i run synclient it tells me that the driver is not loaded.


I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0003 Vendor=046d Product=c52b Version=0111
N: Name="Logitech Unifying Device. Wireless PID:4102"
P: Phys=usb-0000:00:12.0-3:1
S: Sysfs=/devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.2/0003:046D:C52B.0003/0003:046D:C52B.0004/input/input5
U: Uniq=
H: Handlers=sysrq kbd mouse0 event2 
B: PROP=0
B: EV=12001f
B: KEY=3007f 0 0 83ffff17aff32d bf54444600000000 ffff0001 130f978b17c007 ffff73fad941dfff febeffdfffefffff fffffffffffffffe
B: REL=1c3
B: ABS=100000000
B: MSC=10
B: LED=1f

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA ATI HDMI HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card0/input6
U: Uniq=
H: Handlers=event3 
B: PROP=0
B: EV=21
B: SW=140

---

### Post by Tuxclear on 2015-01-02
Yes, probably. *Devices* file also proves that your driver isn't loaded, so it must be a problem from the kernel.
Ubuntu wiki says to report it, but try installing firmware or upgrade the kernel.

---

### Post by inertiaO on 2015-01-02
I successfully upgraded to 3.19 RC2 and now the tap functionality has returned! I had tested 3.18 before and it didn't work, so I am happy now.

Thanks for the help!

---

