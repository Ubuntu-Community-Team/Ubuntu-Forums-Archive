---
title: "sony handycam not detected by Ubuntu"
date: 2012-10-02
forum: Hardware
---

### Post by paulxx on 2012-10-02
I'm a complete beginner with Ubuntu after many years with Windows. It's very confusing but I like it.

I have a Sony Handycam DCR-HC19E pal and I want to transfer video recordings onto my laptop running Ubuntu.

When I plug in the USB cable nothing happens.  When I do the same with another laptop running Windows xp I get a Hardware Wizard which finds a driver and I can then transfer my video recordings.

How can I get Ubuntu to recognise my Sony Handycam.

thanks in advance
paul

---

### Post by sanderj on 2012-10-02
I know nothing about handycams, but the rule of thumb for USB devices not being recognized is this:

unplug the usb device
run 'lsusb'
plug in the usb device
run 'lsusb' again
There should be an extra line ... which is the USB-id of your USB device. Post that line here in this thread, and google for it.

HTH

---

### Post by lisati on 2012-10-02
One thing I've noticed about the cameras and other devices I have is that there's often something you need to do on the device first before the computer (or other device) recognises that the device is there. For example, my HDD DVR won't recognise a camcorder hooked up by Firewire unless I start playing the tape in the camera first. For another camera, which hooks up by USB to my computer, I have to tell the camera to enable the USB connection.

---

### Post by paulxx on 2012-10-03
Thanks Sanderj,

I did what you suggested above and got...
Bus 002 Device 006: ID 054c:00c0 Sony Corp. Handycam DCR-30

I'll try googling it next.

---

### Post by paulxx on 2012-10-03
Hello lisati,

Thanks for the advice. I've tried running the Sony handycam while connected by USB to my laptop running Ubuntu and pressing all the buttons but my Ubuntu desktop does not respond in any way.


Sanderj...
I've googled the line "Bus 002 Device 006: ID 054c:00c0 Sony Corp. Handycam DCR-30" and there seems to be lots of people with the same problem but no solution.

It looks like I shall have to find another solution, perhaps I'll have to go back to windows xp (Windows 7 doesn't have a driver for this model Sony handycam either), then upload my videos to xp, write them to a memory stick/dvd and then read them from Ubuntu.

Anyway, thanks for trying to help.
paul

---

