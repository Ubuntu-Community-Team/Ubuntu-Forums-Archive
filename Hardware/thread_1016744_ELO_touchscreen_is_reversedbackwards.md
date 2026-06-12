---
title: "ELO touchscreen is reversed/backwards"
date: 2008-12-20
forum: Hardware
---

### Post by lilaundgelb on 2008-12-20
I have an ELO USB touchscreen and am running 8.10. Ubuntu automatically recognizes the touchscreen and responds to touch events (without anything appearing in xorg.conf), but the x and y coordinates are reversed: when I touch the left side of the screen, the cursor moves to the right, and when I touch the top, it moves to the bottom.

I have tried installing the evtouch and elographics drivers and modifying xorg.conf (e.g. changing minx, miny, swapx, etc.), but it doesn't seem to have any effect.

Has anybody encountered a similar problem?

---

### Post by mcable1004 on 2008-12-23
I'm having the same problem.  If I figure anything out, I'll post on here.  If you figure it out, would be quite helpful if you posted again as well.

Thanks!

---

### Post by zakattack on 2008-12-23
I've got an elo usb monitor too trying to get it out the door for an xmas present :)
the monitor is an Elo Touch Systems IntelliTouch 2500U
found here:
#grep Elo /proc/bus/input/devices

So far I've tried the evtouch, and elographics drivers with no luck

the elo website looks promising but after following their sketchy instructions neither my keyboard nor touch screen were working.

you can download precompiled binary drivers for multiple distros including 8.04 (which is what I'm running) here...
[http://www.elotouch.com/Support/Downloads/Linux/dnld_linux.asp](http://www.elotouch.com/Support/Downloads/Linux/dnld_linux.asp)

and here are the "instructions" (they don't follow any conventional linux standards that I've seen)
[http://www.elotouch.com/files/install/elo_linux_usb_driver_v3.1_installation_instructions.txt](http://www.elotouch.com/files/install/elo_linux_usb_driver_v3.1_installation_instructions.txt)

my current rc.local has some of their lines commented out
#rmmod elousb
#rmmod usbhid
#sleep 1s
modprobe elousb
#modprobe usbhid

/elo/loadelo
/elo/elodaem


I commented out some of their lines in /etc/modules as well.  I'm not familiar with what is going on in this file but the stuff they had just seemed wrong...
#install usbhid { /sbin/modprobe elousb; } ; /sbin/modprobe --first-time --ignore-install
#usbhid && { /sbin/modprobe/ keybdev; /sbin/modprobe mousedev; /bin/true;}

so i just added this to /etc/modules 
elousb

At this point my curser isn't moving when I touch the screen, but at least my keyboard is working.


if you get an error when trying to run the /elo/cpl about Xmlib
install libmotif3
sudo apt-get install libmotif3

and if you run the calibration tool it may lock everything up with no escape but to cold boot :(
cd /elo
./elova -u


What is odd is the devices...
the elo module creates /dev/elo and /dev/input/elo devices
but they aren't getting data from the kernel
cat < /dev/input/event3
or
cat </dev/input/mouse2
both spew out binary junk when I touch the screen.
but...
cat < /dev/input/elo
doesn't spew anything. I've tried event3 and mouse2 in xorg.conf for the device, but to no avail.



I'm going to go back through the instructions with a fine tooth comb... will update with what I find.
Z

---

### Post by dougbeatty on 2009-05-03
As of 8.10 (Intrepid Ibex), it appears that Elo touch screens (or touch monitors -- I don't know if there is a technical difference) are supported out-of-the-box without the need to install any further packages or modify xorg.conf.  Unfortunately, my monitor ("Elo TouchSystems, Inc. Elo TouchSystems 2700 IntelliTouch(r) USB Touchmonitor Interface") has the reversed/backwards/opposite cursor problem.  The properties in evdev to re-calibrate the screen weren't on my 8.10 system.  I resolved this by installing 9.04 (Jaunty Jackalope) and making the change below (of course replacing the name of my monitor to whatever yours is):

Find the name of your monitor:
```
cat /proc/bus/input/devices
...
I: Bus=0003 Vendor=04e7 Product=0020 Version=0100
N: Name="Elo TouchSystems, Inc. Elo TouchSystems 2700 IntelliTouch(r) USB Touchm
onitor Interface"
P: Phys=usb-0000:00:1d.0-1/input0
...
```To see the current properties:
```
xinput list-props \
"Elo TouchSystems, Inc. Elo TouchSystems 2700 IntelliTouch(r) USB Touchmonitor Interface"

```To invert the axes:
```
xinput set-int-prop \
"Elo TouchSystems, Inc. Elo TouchSystems 2700 IntelliTouch(r) USB Touchmonitor Interface" \
"Evdev Axis Inversion" 8 1 1

```

---

### Post by rthawkcom on 2009-06-22
Having the same issue on 9.04.  Mine says:

I: Bus=0003 Vendor=0eef Product=0001 Version=0210
N: Name="eGalax Inc. USB TouchController"
P: Phys=usb-0000:00:1d.1-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input5
U: Uniq=
H: Handlers=mouse1 event5
B: EV=1b
B: KEY=401 0 30000 0 0 0 0 0 0 0 0
B: ABS=f
B: MSC=10

But when I enter:
xinput list-props  "eGalax Inc. USB TouchController"
unable to find device eGalax Inc. USB TouchController

**BROKEN!!!  **

Are there any plans to fix touch screen monitor support?  Touch screens are getting cheap.  More and more people are going to have this problem.

---

### Post by prsmk on 2009-11-13
> **rthawkcom said:**
> Having the same issue on 9.04.  Mine says:

I: Bus=0003 Vendor=0eef Product=0001 Version=0210
N: Name="eGalax Inc. USB TouchController"
P: Phys=usb-0000:00:1d.1-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input5
U: Uniq=
H: Handlers=mouse1 event5
B: EV=1b
B: KEY=401 0 30000 0 0 0 0 0 0 0 0
B: ABS=f
B: MSC=10

But when I enter:
xinput list-props  "eGalax Inc. USB TouchController"
unable to find device eGalax Inc. USB TouchController

**BROKEN!!!  **

Are there any plans to fix touch screen monitor support?  Touch screens are getting cheap.  More and more people are going to have this problem.


Contact Elo's Tech support and request a driver for Ubuntu 9.04 (2.6.28-11-generic) distribution.

[http://www.elotouch.com/Forms/Support/tech_sup_us.asp](http://www.elotouch.com/Forms/Support/tech_sup_us.asp)

---

