---
title: "Touchpad for Gigabyte SP13 not working"
date: 2010-04-16
forum: Hardware
---

### Post by owls on 2010-04-16
I have a Gigabyte SP13 with an Intel CULV (Consumer Ultra-Low Voltage) processor notebook and the touch pad is not working. Nothing shows up in the /proc/bus/input/devices list that would be a touchpad. Using an external Logitech mouse for the moment.

Tried Ubuntu 9.10 with updates with no luck and now have 10.04 with updates.

```
cat /proc/bus/input/devices 
I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=3
B: KEY=4000 0 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
U: Uniq=
H: Handlers=event2 
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=3
B: KEY=10000000000000 0

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input4
U: Uniq=
H: Handlers=mouse0 event4 
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=120013
B: KEY=402000000 3803078f800d001 feffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=046d Product=c03e Version=0110
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:1d.0-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input6
U: Uniq=
H: Handlers=mouse1 event6 
B: EV=17
B: KEY=70000 0 0 0 0
B: REL=103
B: MSC=10

I: Bus=0003 Vendor=5986 Product=0217 Version=0806
N: Name="USB 2.0 Camera"
P: Phys=usb-0000:00:1d.7-5/button
S: Sysfs=/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input8
U: Uniq=
H: Handlers=kbd event8 
B: EV=3
B: KEY=3f000b00000000 0 0 0

I: Bus=0001 Vendor=10ec Product=0269 Version=0001
N: Name="HDA Digital PCBeep"
P: Phys=card0/codec#0/beep0
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/input/input9
U: Uniq=
H: Handlers=kbd event9 
B: EV=40001
B: SND=6

```

---

### Post by adum68 on 2010-04-24
Bought the same laptop. Adding the 'i8042.noloop=1'kernel boot parameter, as mentioned here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/270611](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/270611)
fixed the problem.

On Lucid 10.04 (installed the RC just today) proceed as follows:
1) sudo vi /etc/default/grub
2) scroll down to the line saying GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" and change it to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.noloop=1"
[note: in other places you may find the advice to add the i8042.nomux=1 option but that didn't seem to work for me.]
3) save and quit, run sudo update-grub and reboot

Touchpad should be working now, and you should also be able to adjust some settings in system->preferences->mouse

Good luck.

---

### Post by owls on 2010-05-04
i8042.noloop=1 worked! thanks!

wondering if you have a suspend issue too? my sp13 goes to sleep anytime i unplug it from or plug it into the AC

---

### Post by adum68 on 2010-05-06
Yes, same problem. The acpi system and/or the gnome power manager might receive a "lid" event, have to do some more research when I get the chance...

As a simple workaround, go to System->Preferences->Power Management and tell the Gnome Power Manager to blank the screen when the lid is closed (both on AC and on battery).

At least the laptop doesn't suspend anymore, it just blanks the screen when you unplug the power chord. Hit the shift key and you're ready to go again.

---

### Post by owls on 2010-05-26
still havent resolved the suspend/ac issue. bump :confused:

---

### Post by Zatarhi on 2010-06-08
Not a fix, but a workaround:
   Find your way to Power Management via Preferences or the Control Center.
   Under both the AC and Battery tabs, change 'When Laptop Lid is Closed' to 'Blank Screen'.
...once that's set, when unplugging or plugging in your laptop the screen will blank, but it will not hibernate or sleep.  A quick flick of the touchpad will fire the screen right back up.

Hope that helps!

---

### Post by Zatarhi on 2010-06-08
Oops, that was already posted.  Nevermind!

---

