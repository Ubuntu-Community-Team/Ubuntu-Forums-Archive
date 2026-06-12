---
title: "USB mouse/keyboard don't work immediatly on login since last update"
date: 2009-06-21
forum: Hardware
---

### Post by ge0ffrey on 2009-06-21
I've been on Ubuntu 9.04 a while, coming from 8.10.
I frequently pull in all updates.
A couple of days ago, I pulled in all the latest updates and it needed to restart (kernel upgrade I think). Since then I have this very annoying problem:

When I start up, the ubuntu logo at some point dissappears and I get some messages about usb. The startup is taking a lot longer: it's clear that it's trying something with usb and a timeout occurs. That happens 4 times.
Then when I get to the login screen, neither my mouse nor my keyboard works. It takes about a minute before they start working.

It's a Microsoft USB mouse and Microsoft USB keyboard, neither are wireless.
At shutdown I get this message when the logo dissappears:
usb 5-1: device description read/64 error -110
usb 5-1: device description read/64 error -110
usb 5-1: device description read/64 error -110
usb 5-1: device description read/64 error -110
usb 5-1: device description read/8 error -110
usb 5-1: device description read/8 error -110
usb 5-1: device description read/8 error -110
usb 5-1: device description read/8 error -110

I've seen the same problem happen on 8.04, over a year ago on my old computer, but I figured they fixed it: apparently they didn't.

---

### Post by ge0ffrey on 2009-06-21
I filed a regression issue:
[https://bugs.launchpad.net/ubuntu/+bug/390199]("https://bugs.launchpad.net/ubuntu/+bug/390199")

---

### Post by ajgreeny on 2009-06-21
This may make no difference at all, but is worth trying I think, if you have not already done so.

Go to your BIOS and in that see if there is a Legacy USB setting that can be enabled.  I have read that it can make a difference on some hardware which is having USB keyboard and mouse problems.

---

### Post by ge0ffrey on 2009-06-22
The USB keyboard is about 6 months old, that's not really legacy. It was the only non-wireless model they had though.

---

### Post by ajgreeny on 2009-06-22
The legacy usb support I suggested enabling, has nothing to do with the keyboard or mouse, it's more about the motherboard hardware, so I still think it is worth trying.

---

