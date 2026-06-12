---
title: "Make all mouse buttons work?"
date: 2008-05-12
forum: Hardware
---

### Post by TB2 on 2008-05-12
Hi,

I bought a Trust MI-6950R mouse and hoocked it up to my laptop. It's a nice mouse actually, and it pretty much worked out of the box, except for horizontal scrolling and those two "zoom buttons" on the left. See this picture:

[img]http://www.qcomp.sk/imgcache/473/at21718261.jpg[/img]

I installed the evdev driver, and then I only had vertical cursor movement - a known bug in the evdev version which is in the repos. I compiled and installed the latest evdev I was able to find, and now that bug is gone. I also have horizontal scrolling (tilting the mouse wheel left and right). But the two zoom buttons are still not working. xev doesn't even pick up anything when I press those buttons. This is what I have in xorg.xonf:

```
Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "evdev"
        Option      "Device" "/dev/input/by-id/usb-04fc_USB_Multi-Smart_Mouse-event-mouse"
        Option      "Name" "Trust MI-6950R"
EndSection
```
I've gone through several "how-to-get-my-mouse-buttons-working" threads and wikis but I can't find a solution. Any idea on how to get the last two buttons working?

Thanks!

---

### Post by lorem_ipsum on 2009-01-05
Hi,

I have a Trust MI-4930Rp. I followed the information on a similar post from Endy regarding a Logitech multibutton mouse:  "Configuring Logitech mice (mx500, etc)", [http://ubuntuforums.org/showthread.php?t=65471](http://ubuntuforums.org/showthread.php?t=65471)

Going through the steps, my xorg.conf file ended up with the following entry:
Section "InputDevice"
        Identifier    "Configured Mouse"
        Driver        "mouse"
    Option        "Protocol"        "evdev"
    Option        "Dev Name"        "MLK Trust Mouse 15315"
    Option        "Dev Phys"        "usb-*/input0"
        Option        "Device"        "/dev/input/event9"
    Option        "Buttons"        "10"
    Option        "ZAxisMapping"        "4 5"
EndSection

This appears to have done the trick.

---

### Post by crazi_man on 2009-03-15
Hi
I've recently switched to Ubuntu and I have a mouse similar to the one pictured above (mine is a Trust wireless optical mouse MI-4950R).
I'm a complete Ubuntu noob, so you'll have to bear with me.
I can't seem to get the zoom buttons to work inspite of following the steps above. (although the wheel tilt function worked fine for me out of the box)
Here's what I put in my xorg.conf file (there was no entry in there already for a mouse, so i whacked this on at the end of the text)

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "Protocol" "evdev"
Option "Dev Name" "MLK Trust Mouse 15399"
Option "Dev Phys" "usb-*/input0"
Option "Device" "/dev/input/event9"
Option "Buttons" "10"
Option "ZAxisMapping" "4 5"
EndSection

I restarted the system and tried out the button in firefox......no joy.
Any other settings I need to mess with? Any idea why it isn't working?
I's appreciate any help here.

Also: when i type       xev | grep ', button'      in terminal to check the mouse buttons, nothing comes up when i press the zoom buttons.

---

### Post by crazi_man on 2009-03-15
Oh and another thing:
Is there any way to get the forward/back buttons working in Nautilus?
I tried this with no luck: [http://gaarai.com/2009/02/13/navigate-in-ubuntu-nautilus-using-the-mouse/](http://gaarai.com/2009/02/13/navigate-in-ubuntu-nautilus-using-the-mouse/)

---

### Post by derdud on 2009-04-24
I hate to resurrect old threads, but what happened with this? I also have a 6950r and I can't seem to get all of the buttons working. The mouse device info appears as:

```
I: Bus=0003 Vendor=04fc Product=0801 Version=0111
N: Name="USB Multi-Smart Mouse"
P: Phys=usb-0000:00:12.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.0/input/input4
U: Uniq=
H: Handlers=kbd mouse2 event4
B: EV=1f
B: KEY=837fff002c3027 bf00444400000000 f1f0001 f848a27c000 667bfad9415fed 8e000000000000 0
B: REL=1c3
B: ABS=100000000
B: MSC=10
```

So I've tried using this in my xorg.conf:

```
Section "InputDevice"
      Identifier "Configured Mouse"
      Driver "mouse"
      Option "Protocol" "evdev"
      Option "Dev Name" "USB Multi-Smart Mouse"
      Option "Dev Phys" "usb-*/input0"
      Option "Device" "/dev/input/event4"
      Option "Buttons" "11"
      Option "ZAxisMapping" "4 5 6 7"
EndSection
```

When I restart X with that configuration, the mouse stops working completely. The configuration below allows the mouse to work, but only the main features (left and right mouse buttons, scroll wheel up/down) work. 

```
Section "InputDevice"
      Identifier "Configured Mouse"
      Driver "mouse"
      Option "CorePointer"
EndSection
```

---

### Post by tomski on 2009-05-22
it would appear that the new version of xorg no longer reads the input device sections as they are now handled by HAL
but alas no documentation actually explain how to congfigure them with the new layout!!!!

nice one eh!

if i find out how to do ill post a comment back here

for reference i use a 9 button logitech lx8
of which only scroll and normal 3 buttons work

---

