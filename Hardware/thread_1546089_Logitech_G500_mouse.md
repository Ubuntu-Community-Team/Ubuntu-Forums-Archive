---
title: "Logitech G500 mouse"
date: 2010-08-04
forum: Hardware
---

### Post by TheOneEyedMan on 2010-08-04
I replaced a well worn MX510 Logitech mouse with a Logitech G500 in my Ubuntu 10.04 / lucid lyx machine.All and all I've been satisfied. Unfortunately, the rocker button built into the scroll wheel for side scrolling is acting like a right button click in Matlab and a few other applications. 

I went digging into how these things are configured and I see that no longer can I use /etc/X11/xorg.conf to set it up I have to use something called udev rules, something that seems above my level of expertise. Can someone help me out?

The rocker buttons are I'd like to disable are 4 (top rocker),5 (bottom),6 (left) and 7 (right). If possible I would also like to map button 10 (side red button) to control-r. 

I'm not sure exactly what I need to tell you to help me so please let me know if you need to know anything else.

Thanks!
______________________________________________
Output of xinput get-button-map 4
1 2 3 4 5 6 7 8 9 10 

________________________________________________
Output of cat /proc/bus/input/devices:

I: Bus=0003 Vendor=046d Product=c068 Version=0111
N: Name="Logitech G500"
P: Phys=usb-0000:00:12.1-2/input1
S: Sysfs=/devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.1/input/input6
U: Uniq=CE896418F70018
H: Handlers=kbd event5 
B: EV=10001f
B: KEY=837fff002c3027 bf00444400000000 1 10f848a27c007 ffe67bfad9415fff febeffdfffefffff fffffffffffffffe
B: REL=40
B: ABS=100000000
B: MSC=10

---

### Post by vivedekananda on 2010-08-14
you can disable the buttons 4-5-6-7 with the command
xinput set-button-map 4 1 2 3 0 0 0 0 8 9 10


You can also configure the mouse using the xorg.conf.d but it didn't work for my mouse (probably I have two devices named Logitech USB Receiver):
[http://blog.burlock.org/ubuntu/186--disabling-the-mouse-scroll-wheel-left-and-right-click-for-ubuntu-1004](http://blog.burlock.org/ubuntu/186--disabling-the-mouse-scroll-wheel-left-and-right-click-for-ubuntu-1004)
[https://help.ubuntu.com/community/Logitech_Marblemouse_USB](https://help.ubuntu.com/community/Logitech_Marblemouse_USB)

Funny that there are now so many quite complicated ways how one can configure the devices, instead of the good old simple xorg.conf file.

---

