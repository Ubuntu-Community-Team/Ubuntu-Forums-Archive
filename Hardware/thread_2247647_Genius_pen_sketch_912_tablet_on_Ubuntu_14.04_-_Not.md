---
title: "Genius pen sketch 9*12 tablet on Ubuntu 14.04 - Not Working"
date: 2014-10-09
forum: Hardware
---

### Post by teen_eagle on 2014-10-09
Hey, I tried to use my [Genius pen sketch 9*12 tablet]("http://www.amazon.com/Genius-PenSketch-PhotoShop-Cordless-rubber-coated/dp/B000COKZJK/ref=pd_sxp_f_pt") on Ubuntu 14.04, but all the solutions out there didn't seem to work,

 First it seems there is no wizardpen release for ubuntu 14.04, am i wrong ?!

Second, my tablet's light is responding to both mouse and pen, none of them moves the pointer but only the mouse can click with the 3 buttons and even scrolls !,
However when i use the command **lsusb** in the terminal it detect a new hardware but doesnt identify it as a tablet "first line" :
> Bus 002 Device 004: ID 5543:0008 UC-Logic Technology Corp. 
Bus 002 Device 053: ID 0461:4d22 Primax Electronics, Ltd 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 1bcf:2c18 Sunplus Innovation Technology Inc. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

is there anything i can do to solve this ? any idea? 
Thank you, your help will be very appreciated.

---

### Post by teen_eagle on 2014-10-10
up !

---

### Post by lazarj on 2014-12-27
Hi all!

My niece just got a **Genius Pensketch M912** for Christmas. After two nights of struggling with it I'm really interested whether *anyone* succeeded to make it work under Ubuntu 14.04? Teh internets sais that the last succesful (or at least documented) attempt with it was done with 10.10.

It is pretty natural behaviour NOT to seek for answers if everything is okay with your device. But who knows. If you have a working config, please post it!

**The stake is high**, if I won't success within a few days, her laptop will be downgraded to windows. (No, really. Our prime minster recently sold out my country to M$, so my niece can get windows for a handful of peanuts - legally. And I see myself as a virus buster soon. Bleh. I told, stakes are high.)

I have partial results with wizardpen driver. It compiles like a charm, I could even make xorg config files to load the wizardpen driver for "it". (Well, at least make partially work the stylus - no drawing == no Z axis I think but with some button bindings, no tablet buttons, no moving mouse). Xorg detects the tablet with errors, MySketch freezes, gimp is stable.
Well, I still lack of heavy skills in xorg configuration, button mapping, etc. However the above implies that there is some hope to make this thing work. I keep trying, but I assume I'll give it up this night or tomorrow. I tend to read too much complicated things (kernel, hid, etc) so the project may be beyond my current linux skills. Current question is about **feasibility**.

Thanks in advance, again!

---

### Post by jonas-h331 on 2015-08-18
I guess all these threads (about Genius Pensketch 912) are dead by now but anyway I'll try to let you know what I found out.
OK, so the first problem is with the wizardpen driver - I think it just doesn't recognize the tablet. If I look into /var/log/Xorg.0.log this is what I see:
```
[  3111.284] (II) config/udev: Adding input device Genius PenSketch M912 (/dev/input/mouse1)[  3111.284] (II) No input driver specified, ignoring this device.
[  3111.284] (II) This device may have been added with another device file.
[  3111.312] (II) config/udev: Adding input device Genius PenSketch M912 (/dev/input/event8)
[  3111.312] (**) Genius PenSketch M912: Applying InputClass "evdev pointer catchall"
[  3111.312] (**) Genius PenSketch M912: Applying InputClass "evdev keyboard catchall"
[  3111.312] (**) Genius PenSketch M912: Applying InputClass "evdev tablet catchall"
[  3111.312] (II) Using input driver 'evdev' for 'Genius PenSketch M912'
[  3111.312] (**) Genius PenSketch M912: always reports core events
[  3111.312] (**) evdev: Genius PenSketch M912: Device: "/dev/input/event8"
[  3111.312] (--) evdev: Genius PenSketch M912: Vendor 0x458 Product 0x5015
[  3111.312] (--) evdev: Genius PenSketch M912: Found 10 mouse buttons
[  3111.312] (--) evdev: Genius PenSketch M912: Found scroll wheel(s)
[  3111.312] (--) evdev: Genius PenSketch M912: Found relative axes
[  3111.313] (--) evdev: Genius PenSketch M912: Found x and y relative axes
[  3111.313] (--) evdev: Genius PenSketch M912: Found absolute axes
[  3111.313] (--) evdev: Genius PenSketch M912: Found x and y absolute axes
[  3111.313] (--) evdev: Genius PenSketch M912: Found absolute tablet.
[  3111.313] (--) evdev: Genius PenSketch M912: Found keys
[  3111.313] (II) evdev: Genius PenSketch M912: Configuring as tablet
[  3111.313] (II) evdev: Genius PenSketch M912: Configuring as keyboard
[  3111.313] (II) evdev: Genius PenSketch M912: Adding scrollwheel support
[  3111.313] (**) evdev: Genius PenSketch M912: YAxisMapping: buttons 4 and 5
[  3111.313] (**) evdev: Genius PenSketch M912: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  3111.313] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb4/4-1/4-1.4/4-1.4:1.0/0003:0458:5015.0007/input/input19/event8"
[  3111.313] (II) XINPUT: Adding extended input device "Genius PenSketch M912" (type: KEYBOARD, id 12)
[  3111.313] (**) Option "xkb_rules" "evdev"
[  3111.313] (**) Option "xkb_model" "pc105"
[  3111.313] (**) Option "xkb_layout" "cz"
[  3111.313] (WW) evdev: Genius PenSketch M912: touchpads, tablets and touchscreens ignore relative axes.
[  3111.314] (II) evdev: Genius PenSketch M912: initialized for absolute axes.
[  3111.314] (**) Genius PenSketch M912: (accel) keeping acceleration scheme 1
[  3111.314] (**) Genius PenSketch M912: (accel) acceleration profile 0
[  3111.314] (**) Genius PenSketch M912: (accel) acceleration factor: 2.000
[  3111.314] (**) Genius PenSketch M912: (accel) acceleration threshold: 4
```
No errors, but also nothing about wizardpen - not even trying.

Anyway I was able to make at least evdev work - without pressure sensitivity of course.
You can use xmodmap to change what buttons on your mouse do. And I found out that when you touch your pen to the tablet, it functions as sort of a "go back button". And for me it outputed signal "8". So this is how I modified the xmodmap command:
```
[COLOR=#333333][FONT=UbuntuMono]xmodmap -e "pointer = "8 2 3 4 5 6 7 1"[/FONT][/COLOR]
```
And it worked. 
Of course my mouse stopped working, because that is a global command and it also changed the settings for my mouse, so I couldn't click, but the evdev driver for the tablet was working (anyway it worked on Ubuntu Studio, now I'm on Kubuntu and I'm having some trouble).
There is also a workaround where you can specify this for just one device, but I was too happy and lazy to do that.

Conclusion?
Didn't make wizardpen work, at least was able to make evdev work.

---

