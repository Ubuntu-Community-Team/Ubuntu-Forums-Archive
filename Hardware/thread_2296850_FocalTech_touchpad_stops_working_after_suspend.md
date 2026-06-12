---
title: "FocalTech touchpad stops working after suspend"
date: 2015-09-29
forum: Hardware
---

### Post by thatoo2 on 2015-09-29
I have an Asus V502LX the persian version of the Asus K501LX.

I have Ubuntu 14.04 installed and the kernel 4.1.6 installed.

I noticed one problem. The Focaltech touchpad is not working after suspending the comnputer.

Here is what I could find about the touchpad in  /proc/bus/input/devices

I: Bus=0011 Vendor=0002 Product=0012 Version=0000
N: Name="FocalTechPS/2 FocalTech FocalTech Touchpad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input5
U: Uniq=
H: Handlers=mouse0 event4 
B: PROP=5
B: EV=b
B: KEY=e520 10000 0 0 0 0
B: ABS=260800000000003

I can deactivate and activate again the touchpad with the hotkey of my keyboard without problem.

I tried a solution given on internet but it doesn't work properly.

I created a file here /etc/pm/sleep.d/0000trackpad
sudo gedit /etc/pm/sleep.d/0000trackpad

and add the following
#!/bin/sh
case "$1" in
    suspend|hibernate)
        modprobe -r psmouse;
    resume|thaw)
        modprobe psmouse;
esac

Now, the computer refuse to suspend. At least, the touchpad keep working so it does something but I can't make my computer sleeping...

I file a bug here about it, [https://bugzilla.kernel.org/show_bug.cgi?id=105231](https://bugzilla.kernel.org/show_bug.cgi?id=105231)

People with a similar problem on a different computer, with an Elantech touchpad are talking about it here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1490130](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1490130)

---

