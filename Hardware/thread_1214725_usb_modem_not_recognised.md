---
title: "usb modem not recognised"
date: 2009-07-16
forum: Hardware
---

### Post by philipluna on 2009-07-16
i have just installed Ubuntu 8.04 on my laptop .Unfortunatlly my orange icon 225 usb modem will not install .it has its own drivers installed and ubuntu pickes them up but when i click on them nothing happens . I have been searching the net all day for a solution with no joy if you have a solution please keep it simple as i am not the brightest apple on the tree when it comes to computers and i am a newbi with Linux

---

### Post by jerrrys on 2009-07-17
have you been here?

[http://www.google.com/search?q=orange+icon+225+usb+modem+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=orange+icon+225+usb+modem+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by varun1786 on 2009-07-19
are you sure ubuntu did not load the drivers by default. I attached my modem and din install anything. Got my connection to work perfectly with **wvdial**.

open up a terminal and try this

$*lsusb*

Check if your modem is listed. If it is lemme knw i can help you config it.

Or else disconnect your modem wait a few seconds and reconnect it. Then open up a terminal and type this

$dmesg | tail

see if ubuntu detects your modem and which port it is connected it to.

---

