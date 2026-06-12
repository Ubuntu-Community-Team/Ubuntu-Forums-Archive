---
title: "Internet Troubles"
date: 2009-03-11
forum: Installation &amp; Upgrades
---

### Post by Grykus on 2009-03-11
Ok, so I heard all these great reviews and stuff about Linux. SO I got myself a CD, and decided to try it out. I liked it alot, and from what I've seen... it would fufill my "Hacker" image.

But what good is a Hacker without internet. So I through in my Sympatico Highspeed Internet Installation CD and went... "F**K!" Because Linux couldn't read the image.

I use a USB Speet Touch Modem. I've heard stories of people using Sympatico on Linux. But it says Windows only. :( I don't own the Internet, I share it with my parents so I can't really switch.


Any suggestions? I will supply any information you need.

---

### Post by ajgreeny on 2009-03-11
> I share it with my parents so I can't really switch.How do you share it ?  If with a wired router, you are probably already connected, but if with wireless, you may have more problems depending on the wireless adapter of your computer.

---

### Post by Grykus on 2009-03-11
It's a strange way of sharing it. When my dad uses it, he unplugs the modem from my computer and plugs it into his. Weird. But it works.

---

### Post by ajgreeny on 2009-03-11
Sorry, can't help any further as I have never heard of the modem.

---

### Post by Grykus on 2009-03-11
The Alcatel Speedtouch USB Modem. It's shaped like a Sting Ray.
Just thought I would throw that out incase it's needed.

Also...
I don't think the Modem is the problem. I think what might be the reason is the CD is in the wrong format. Is there any way I can get Ubuntu to run support for Windows File Formats.

Without internet?

---

### Post by Grykus on 2009-03-12
Bump.

No help from anyone?

---

### Post by Brandon.Viking on 2009-03-12
> **Grykus said:**
> The Alcatel Speedtouch USB Modem. It's shaped like a Sting Ray.
Just thought I would throw that out incase it's needed.


You are right that the driver CD is not going to work. I would be guessing but would think that only Windows drivers are on there.

Is there any other port to connect to the modem than USB? Like a network port (RJ-45 port)?

Not sure if the USB modems work under Linux as I think from memory they use software package to drive the modem to connect to the internet. Linux would have to have a driver for the USB modem.

Bus 001 Device 004: ID 046d:c043 Logitech, Inc. MX320 Laser Mouse
Try something ... plug in the USB modem then open a terminal and use lsusb to get the id of the modem. eg. my mouse is listed as 
Bus 001 Device 004: ID **046d:c043** Logitech, Inc. MX320 Laser Mouse

The id is bold.

From there you could seach the internet to see if Linx supports a device with that ID 

Not much help but at least something to try.

---

### Post by Grykus on 2009-03-12
I wnt into the Terminal, typed lsusb and pressed enter. And it didn't do anything. Didn't even give me an invalid error.

(Sorry, I'm to to this.)

---

### Post by Grykus on 2009-03-12
Bumpity Bump

Boy these forums move fast.

---

### Post by linux_tech on 2009-03-12
go here
[http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html)
follow instructions and post back with specific questions

---

