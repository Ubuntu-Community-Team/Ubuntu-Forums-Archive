---
title: "Detection of PS/2 devices"
date: 2007-08-24
forum: Hardware &amp; Laptops
---

### Post by wj313 on 2007-08-24
Hi forum,

How do I detect if a device is connected to the PS/2 port of a PC with Kernel 2.6?

E.g. the PS/2 mouse port is regocized by the Kernel, but how do I check if a device (mouse) is attached?

Kind regards.

---

### Post by heimo on 2007-08-24
> **wj313 said:**
> E.g. the PS/2 mouse port is regocized by the Kernel, but how do I check if a device (mouse) is attached?

Look on the right side of your keyboard and follow wire from mouse to the back of your computer.

;-) ;-) Sorry, couldn't resist. I've never had any problems attaching PS2 devices (other than with KVM switch), so it's been just plug'n'play. I think there's no such system as with real plug'n'play stuff like PCI cards, so that you could "scan" for PS2 devices (I may be wrong, but this is my understanding). So if you want to see if it's attached and OS gets data, you could do something like cating the device and moving your mouse. (cat /dev/what-ever-ps2-device-name-is). Then you would see garbled text on screen.

What is it that you're trying to achieve? Aren't your PS2 devices functioning?


EDIT: fix typo

---

### Post by wj313 on 2007-08-24
I haven't any problems with PS/2 devices at all - they work properly.

What I want to achieve is the following: How can I tell _FROM REMOTE_ if a PS/2 mouse is connected to a PC? The psaux port is there, sure - but is a mouse connected?

To call the user and tell him: "Please move your mouse right now, so I can do a 'cat /dev/input/mouse' and catch some symbols" is (unfortunately) not an option .. ;-)

---

### Post by heimo on 2007-08-24
> **wj313 said:**
> I haven't any problems with PS/2 devices at all - they work properly.

What I want to achieve is the following: How can I tell _FROM REMOTE_ if a PS/2 mouse is connected to a PC? The psaux port is there, sure - but is a mouse connected?

To call the user and tell him: "Please move your mouse right now, so I can do a 'cat /dev/input/mouse' and catch some symbols" is (unfortunately) not an option .. ;-)

There probably is some reason that programs like mdetect ask you to move your mouse to be able to detect it. Perhaps, I'm guessing, PS/2 support such features that you could read what's connected so that you could scan which devices are connected. I may be wrong, though. Please let me know when you find a way to do it without.

[http://packages.ubuntu.com/feisty/utils/mdetect](http://packages.ubuntu.com/feisty/utils/mdetect)
[http://www.penguin-soft.com/penguin/man/1/mdetect.html](http://www.penguin-soft.com/penguin/man/1/mdetect.html)

---

