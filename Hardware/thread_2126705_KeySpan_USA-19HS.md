---
title: "KeySpan USA-19HS"
date: 2013-03-17
forum: Hardware
---

### Post by garya on 2013-03-17
I'm trying to use a KeySpan USA-19HS serial port adapter on Xubuntu 12.04.  I am using an old HP Compaq NC6000 computer.  For some reason the serial ports don't seem to work correctly with the Ubuntu family.  I'm trying the serial port adapter, and my program can see it, but it doesn't seem to be able to communicate.  Does Xubuntu 12.04 have drivers for the KeySpan USA-19HS?  How can I check?  If not, where can they be found?

Thank you,
Gary

---

### Post by mdecler2 on 2013-06-17
> **garya said:**
> I'm trying to use a KeySpan USA-19HS serial port adapter on Xubuntu 12.04.  I am using an old HP Compaq NC6000 computer.  For some reason the serial ports don't seem to work correctly with the Ubuntu family.  I'm trying the serial port adapter, and my program can see it, but it doesn't seem to be able to communicate.  Does Xubuntu 12.04 have drivers for the KeySpan USA-19HS?  How can I check?  If not, where can they be found?

Thank you,
Gary

Maybe you have a similar problem as I do?  I don't have a solution, but maybe we can compare notes.

I am using the Ubuntu Desktop 12.04 version with the KeySpan USA-19hs device and having no such luck.  I get a mostly consistent kernel panic within a minute of connecting the device.

There seems to be a problem either with the the keyspan driver, the usbserial driver, or both.  The following syscalls seem to be very consistent with each panic occurrence I have seen: serial_down, tty_port_hangup, keyspan_close.

There have been times where the kernel doesn't panic after I connect the device.  What I notice in those cases is a very limited amount of serial communication, such that when I run jpnevulator to read output from the device, I get a few bytes of data and no more, even though data from the other end is streaming constantly.  

I originally experienced the problem on 10.10 before I upgraded, and I have experienced the same panic in 12.04 kernel patches, up to today 6/17/2013.

I really don't know how to diagnose the problem, I am kind of new at this.  There are a lot of setup options for serial ports, and I am sure have been around for a long time, so I am going to do some investigation into that.

I posted my bug here:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/1018241](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/1018241)

---

