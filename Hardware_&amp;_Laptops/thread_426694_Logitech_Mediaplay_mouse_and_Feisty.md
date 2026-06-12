---
title: "Logitech Mediaplay mouse and Feisty"
date: 2007-04-28
forum: Hardware &amp; Laptops
---

### Post by FeitaKveita on 2007-04-28
Hi there! 

I'm a Linux newbie, and have done two installs of Feisty on my laptop. When I installed it the first time all the buttons on my Mediaplay mouse worked perfectly without setting anything up. I could use stop, prev/next, volume and so on with Rythmbox. But it doesn't work on my current install. I know there are some drivers for Logitech mouses out there, but obviously there has to be built in support for my mouse since it worked the first time. I'm sure it's just something I have to set up in xorg.conf. 
Anyone have an idea on what to do? Anyone with a working similar mouse want to post their xorg.conf?

Thanks!

---

### Post by ZeroXtreme on 2007-04-30
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "evdev"
        Option          "CorePointer"
        Option          "Dev Name"      "Logitech USB RECEIVER"
        Option          "Dev Phys"      "usb-0000:00:1d.0-1/input0"
        Option          "Device"        "/dev/input/event2"
        Option          "Buttons"       "17"
        Option          "ZAxisMapping"  "4 5"
        Option          "Resolution"    "800"
EndSection

You may have different values for the "Dev Phys" and "Device", to find out run "cat /proc/bus/input/devices" then scroll through it and look for the logitech entry.

I have this running on my laptop with Feisty and my MediaPlay Mouse, but still mapping the other buttons, what works is the scroll, back, forward and 2 primary buttons.

Hope this helps as a start.

---

### Post by tenshi-no-shi on 2007-05-15
sweet I have been looking for a way to get my MediaPlay mouse working for a long time and this is the first post I have seen that has actually made this simple. though I would use "usb-*/input0" for simplicity.

---

### Post by tenshi-no-shi on 2007-05-30
Well just an update. I had to stop using that xorg configuration because it was stopping xserver from starting. 

I just found something out though, using the standard mouse driver set to Explorer Mouse almost everything works. in fact the volume buttons work without configuration

---

### Post by 19pacman73 on 2007-05-31
where did you set it to be explorer mouse?

thnx

---

