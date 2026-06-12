---
title: "Logitech vx revolution problem after Heron upgrade"
date: 2008-06-16
forum: Hardware
---

### Post by tomWright on 2008-06-16
OK, folks. I still do not have a working 5 button mouse.

So I have a question for Linux developers:

WTF?

The mouse is the most important interface device after the keyboard and display.

Millions of mice are in use with more than 3 buttons. Yet Linux cannot seem to get this simple device correct. I see solutions that involve more command line work that I needed to do to install a Mitsumi 1x CD Rom under Win3.1! 

So does this mean Linux has not yet caught up to Win3.1? Yes. I does.
If Linux can not get the basic interface correct, the majority of users will abandon it without EVER looking past that and to the other things that developers seem more interested in.

Mice may not be as cool as super-video interfaces or browser tricks, but it is so basic that without them you will NEVER compete with Windows.

So now the question is: Does the Linux community really want to compete with Windows and become friendly and welcoming to non-techie folks, or does the Linux community want to remain an elitist clic that likes to look down on the great unwashed peons of the Windows world?  

If you want to compete, you have to get the basics fixed first.





---------------- original below

Hello, Just upgraded from Dapper to Heron. Using an HP ZD8000.

Mouse is Logitech vx revolution RF laser. The antenna is always in the same usb port.

This mouse worked with 5 buttons under Dapper, but I can only get 3 buttons under Heron.

I have been through a bunch of threads, but the solutions seem awful complicated, silly even. I cannot believe that the developers made mouse configuration more complicated and difficult rather than easier, so we all must be missing something. If they did, they are going in exactly the wrong direction to encourage folks to switch away from MS.


Here is my xorg.conf:
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Buttons"       "7"
        Option          "Protocol"      "ExplorerPS/2"
        Option          "ButtonMapping" "1 2 3 7 6"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "false"
EndSection

...

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        Inputdevice     "stylus"        "SendCoreEvents"
        Inputdevice     "cursor"        "SendCoreEvents"
        Inputdevice     "eraser"        "SendCoreEvents"
        Inputdevice     "Synaptics Touchpad"
EndSection




Here is all the mouse related output from "cat /proc/bus/input/devices". I have also included the touchpad entry:

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

...

I: Bus=0011 Vendor=0002 Product=0007 Version=00b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input8
U: Uniq=
H: Handlers=mouse1 event8 
B: EV=b
B: KEY=6420 0 70000 0 0 0 0 0 0 0 0
B: ABS=11000003

I: Bus=0003 Vendor=046d Product=c518 Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.1-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/input/input9
U: Uniq=
H: Handlers=mouse2 event9 
B: EV=17
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143
B: MSC=10

I: Bus=0003 Vendor=046d Product=c518 Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.1-1/input1
S: Sysfs=/devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.1/input/input10
U: Uniq=
H: Handlers=kbd event10 
B: EV=1f
B: KEY=37fff ac3027 bf004444 0 0 1 f84 8a37c000 667bfa d9415fed 8e0000 0 0 0
B: REL=40
B: ABS=1 0
B: MSC=10



For some reason, there is an entry for a macintosh emulator, even though this is not a mac and there is no mac mouse.
Also, there are TWO entries for the mouse, but using input1 and input0. Could this cause a conflict?

Using xev, the mouse buttons issue the following events:
Left: Button 1
Wheel Click: Button 2
Right: Button 3
Up: Button 4
Down: Button 5
Forward: Button 6
Back: Button 7


Has anyone figured out a way to configure a mouse in less than 1000 command line steps? (jk)
:confused:

---

### Post by tomWright on 2008-06-21
bump

---

### Post by tamoneya on 2008-06-23
[http://ubuntuforums.org/showthread.php?p=2727025](http://ubuntuforums.org/showthread.php?p=2727025)
That worked well for my VX.

---

