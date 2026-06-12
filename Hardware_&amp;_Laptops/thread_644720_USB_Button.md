---
title: "USB Button"
date: 2007-12-19
forum: Hardware &amp; Laptops
---

### Post by Ric_ on 2007-12-19
Hi all i have a nice new shiny USB panic button. Does anyone have this working on theior linux system? Any pointers would be great.

Ric

---

### Post by Rhubarb on 2007-12-19
Have a look in System --> Preferences --> hardware information to see if ubuntu recognises it.
Also, unplug the button, go into System --> Administration --> System Log, then plug in your button to see how it recognises it.

It could be a simple HID keyboard sending a special keyboard scanning code, who knows.
I've done a quick search on the internet and have only found that it works for windows users only.

---

### Post by soupmonster on 2008-01-12
I just got one of these, and I'm trying to get it to work in Gutsy. When plugged in, the panic button shows up in Hardware information as a USB HID interface device, with a info.parent string of /org/freedesktop/Hal/devices/usb_device_1130_202_noserial. Looking at the system logs, this registers itself fine when plugged in and taken out, but I guess as no-one has written a driver to detect the button press, nothing happens when you press it, not in syslog or kern.log or debug.

If I knew the first bit about C, C++ or linux kernel usb driver writing, I imagine it would be relatively trivial to get this emulating a key press. Ideally though, it would be awesome if someone could create a little applet to enable to launch commands when the button press is detected.

If anyone could point the way as to where to start, I wouldn't mind getting to grips with writing a driver, I always wanted to learn C anyway. Or maybe I can just hope for some magical driver to appear in Hardy. Yeah...

---

### Post by Rhubarb on 2008-01-20
If it just returns a special charactor / keyboard scan code, you could bind that key to a bash script that could execute something.
But alas I really don't know.
It might pay to do a little research on the net, you might be able to program it in python rather than c.

A good example is **pymissile** that can be found in the ubuntu repositories:
[I]Control Marks and Spencer USB Missile Launcher
Provide curses interface to control a Marks and Spencer USB Missile Launcher,
as well as a motion control script to allow a webcamera to control the
launcher.
 Homepage: [http://scott.weston.id.au/software/pymissile/](http://scott.weston.id.au/software/pymissile/)[/I]

If you have a look at the source code of this and perhaps talk to scott about it, you might be able to make up a simple app to do it.  After all, it is just a peripheral with only 1 button on it.

---

### Post by bkendinibilir on 2008-07-23
I wrote a perl module for using the USB Panic Button under Unix: [http://search.cpan.org/search?query=Device-USB-Panic](http://search.cpan.org/search?query=Device-USB-Panic)

Full instruction for setup under debian documented in the README file.

Have Fun :)

---

