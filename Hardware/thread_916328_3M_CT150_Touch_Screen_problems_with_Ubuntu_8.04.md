---
title: "3M CT150 Touch Screen problems with Ubuntu 8.04"
date: 2008-09-10
forum: Hardware
---

### Post by d2army on 2008-09-10
Hi there,

I have a 3M CT150 touch screen device connected to my Ubuntu 8.04 machine via USB. It seems like the innate microtouch_drv.so driver that comes with Ubuntu is able to recongnize the screen.

Also, when I do "cat /proc/bus/input/devices" , I see the screen there : 

I: Bus=0003 Vendor=0596 Product=0001 Version=0410
N: Name="3M 3M USB Touchscreen - EX II"
P: Phys=usb-0000:00:1d.0-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input4
U: Uniq=
H: Handlers=mouse1 event4 
B: EV=b
B: KEY=400 0 0 0 0 0 0 0 0 0 0
B: ABS=3

I noticed something amiss in the X11 logs (/var/log/Xorg.0.log ) :

(**) Option "Device" "/dev/input/event4"
(**) Option "MinX" "-7185"
(**) Option "MaxX" "-7185"
(**) Option "MinY" "7013"
(**) Option "MaxY" "2474"
Unable to query/initialize MicroTouch hardware.
(EE) PreInit failed for input device "3MTouchScreen"
(II) UnloadModule: "microtouch"


The MinX to MaxY values are calculated using the TouchCal calibration program from SourceForge.

I don't know why the micro-touch driver will fail and unload.

Even though it looks like it failed, I can still use the touch screen. Except that the X-axis is flipped and the pointer is extremely jittery ( Y axis is fine )

Has anyone had any experience with these touch screen driver setups?

Thanks
IS

---

### Post by damko on 2008-10-22
Hi I'm fighting with the same monitor too (mine is 17" but it's the same).
Did you find a way to fix the issue?
Could you post your xorg.conf file?

thank you

---

