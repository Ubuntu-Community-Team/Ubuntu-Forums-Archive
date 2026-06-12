---
title: "Del Latitude's Touchpad Freaks out"
date: 2006-02-01
forum: Hardware &amp; Laptops
---

### Post by CPUFreak91 on 2006-02-01
I just installed Ubuntu on my sisters just-arrived used Dell Latitude laptop. Unfortunately while playing a game the computer jammed (I need to turn down some settings). My father decided to apply brute force to remove the battery (when there was a perfectly good switch right next to it). I'm pretty sure this broke the touchpad (as it looks like it has been bent in the process of taking out the battery).

How can I disable the touchpad and keep the button mouse working to prove my suspicions?
Whenever any mouse is used (Touchpad, Buttonmouse or external USB mouse) the pointer always goes up to the top right of the screen and it takes a lot of persuasion to move it somewhere else and then it moves back up to the right corner again randomly or by moving any mouse. Windows is not installed on this laptop anymore so I can't say that it's a linux problem either.

EDIT> The computer is running Breezy with a minimal KDE 3.4 installation off the web

---

### Post by geek.de.nz on 2006-04-20
I have got the exact same problem on my touchpad (Dell Latitude P4 1.2GHz), but I'm sure the touchpad is not broken because it works fine (both touchpad and USB mouse) in windows, which is on the same machine.

I've read a lot of threads, but nothing seems to help...

I remember that I installed Knoppix once before and I think I had the same problem and did fix it by changing the protocol, but I do not remember what protocol it was and I' also not entirely sure of this.

In /etc/X11/xorg.conf
```

...
Option "Protocol" "ImPS/2"
...

```

What are the possible values or where can I find them?

---

### Post by MarkHn on 2006-04-20
I have a similar problem. My mouse touchpad has gone crazy since i upgraded to Dapper.  I can't use it any more. With the slightest touch, it opens applications, drags icons around the screen. If i click on a terminal window, it is likely to paste in anything to the command prompt, including random text from any other open windows or firefox browsers. It works fine in windows XP, so I know the touchpad is ok.

---

### Post by CPUFreak91 on 2006-04-20
[QUOTE=MarkHn]I have a similar problem. My mouse touchpad has gone crazy since i upgraded to Dapper.  I can't use it any more. With the slightest touch, it opens applications, drags icons around the screen. If i click on a terminal window, it is likely to paste in anything to the command prompt, including random text from any other open windows or firefox browsers. It works fine in windows XP, so I know the touchpad is ok.[/QUOTE]

Oh well, it turns out that the mouse was bad after all... this really lowers the sale price. :(

---

### Post by geek.de.nz on 2006-04-21
Just doing some research on this now. Seems to be a problem with the 2.6 Kernel Version. A quick workaround if you have a USB or other mouse you can connect to your laptop:
Just disable the touchpad in your Bios and connect your USB or other mouse to your laptop. That should work for the moment. Works for me. Be sure to turn the mouse to serial though. ;)

I'll read up on the Kernel stuff which I found on the net and will keep you updated if I find something.

Maybe you guys can sieve the net as well. Try the following keywords (google):
Linux Laptop kernel 2.6 touchpad
etc, instead of just on Ubuntu. Hope that helps and hope that other people reading this will do some research themselves, because this matter is not really discussed on the Ubuntu forums yet.

Look especially for Debian etc, because Ubuntu is based on Debian, but you probably know that.

---

### Post by CPUFreak91 on 2006-04-21
[QUOTE=geek.de.nz]Just doing some research on this now. Seems to be a problem with the 2.6 Kernel Version. A quick workaround if you have a USB or other mouse you can connect to your laptop:
Just disable the touchpad in your Bios and connect your USB or other mouse to your laptop. That should work for the moment. Works for me. Be sure to turn the mouse to serial though. ;)

I'll read up on the Kernel stuff which I found on the net and will keep you updated if I find something.

Maybe you guys can sieve the net as well. Try the following keywords (google):
Linux Laptop kernel 2.6 touchpad
etc, instead of just on Ubuntu. Hope that helps and hope that other people reading this will do some research themselves, because this matter is not really discussed on the Ubuntu forums yet.

Look especially for Debian etc, because Ubuntu is based on Debian, but you probably know that.[/QUOTE]

Thanks but don't trouble yourself anymore.. it doesn't work in Windoze either.
We got around the problem by disbling the mouse in the bios... but no one wants to buy it now with an external mouse or a bad touchpad. :p

---

### Post by geek.de.nz on 2006-04-23
If I use a 2.4 Kernel distro such as Knoppix and boot it from CD, both touchpad and USB mouse work!

However, I've extensively (since a couple of days) searched the net and found [http://www.ee.oulu.fi/~tuukkat/tmp/linux-2.6.7-userdev.20040625.patch](http://www.ee.oulu.fi/~tuukkat/tmp/linux-2.6.7-userdev.20040625.patch) which apparently solves the problem by letting the 2.6 kernel behave like the 2.4 Kernel with respect to input devices, such as the touchpad. I haven't been able to compile the 2.6.6 kernel with the appropriate patch on my Ubuntu 5.10 Laptop. If someone here knows how to upgrade the patch, so that it can be applied to the 2.6.12 Kernel which ships with Ubuntu 5.10, that would greatly be appreciated.

Otherwise, does anyone know if the new kernel versions would fix this error?

---

### Post by geek.de.nz on 2006-04-28
OK, after hours and hours of searching on the net, an email conversation with Tuukka Toivonen, the writer of SERIO_USERDEV, I found out a (dirty?) solution or better what the problem is:

The 2.6 kernel seems to automatically load 2 drivers (at least on my Dell Latitude C610). 

```

#cat /proc/bus/input/devices
...
I: Bus=0011 Vendor=0002 Product=0007 Version=0000
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
H: Handlers=mouse1 event2 ts1
B: EV=b
B: KEY=6420 0 70000 0 0 0 0 0 0 0 0
B: ABS=11000003

I: Bus=0011 Vendor=0002 Product=0001 Version=0000
N: Name="PS/2 Generic Mouse"
P: Phys=synaptics-pt/serio0/input0
H: Handlers=mouse2 event3 ts2
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

```

You can just avoid using the "PS/2 Generic Mouse" driver by using /dev/input/mouseX drivers in /etc/X11/xorg.conf (and if you need it in gpm). So instead of /dev/input/mice or /dev/psaux.

So, to make it easy. Just delete all the 'Section "InputDevice"' sections from your /etc/X11/xorg.conf and add the following:

```

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
#    Driver        "mouse"
    Option        "CorePointer"
    Option        "SendCoreEvents"    "true"
#    Option        "Device"        "/dev/psaux"
    Option        "Device"        "/dev/input/mouse1"
    Option        "Protocol"        "auto-dev"
#    Option        "Protocol"        "ExplorerPS/2"
#    Option        "HorizScrollDelta"    "0"
    Option        "MaxTapTime"        "180"
EndSection

Section "InputDevice"
        Identifier      "USB Mouse"
    #Identifier  "PS/2 Mouse"
        Driver          "mouse"
        #Option          "Device"                "/dev/input/mice"
        Option          "Device"                "/dev/input/mouse0"
    Option        "SendCoreEvents"    "true"
        Option          "Protocol"              "IMPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Buttons"               "5"
EndSection

```

If that doesn't work on your system, /dev/input/mouse0 might not be the USB mouse, but the touchpad. So, you need to maybe experiment a bit. But anyway, this should be a solution. However, there will still be an unneccessary driver loaded. I do not know how to unload this. 'rmmod psmouse' in a console unloaded both drivers, so that the touchpad wouldn't work at all, but I don't know how to remove just the "PS/2 Generic Mouse" driver. If someone knows how to remove that, please tell.

Anyway, my touchpad now works, even with scrolling at the sidebar :-D.

As soon as I know howto do this, I might write an updated howto on this subject since it doesn't seem to exist.

---

