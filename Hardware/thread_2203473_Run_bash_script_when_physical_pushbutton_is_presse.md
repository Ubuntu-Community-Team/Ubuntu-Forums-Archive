---
title: "Run bash script when physical pushbutton is pressed?"
date: 2014-02-03
forum: Hardware
---

### Post by Cookie Guru on 2014-02-03
I have two physical pushbutton switches.  They can be either NC or NO.  I want to run a bash script when either of these are pressed (different script for each switch).

The box in question is headless running 13.10 server.  I have a plethora of USB ports, an untested serial header, and a pair of PS/2 ports.

Arduino could definitely do this but that seems like overkill.

---

### Post by tgalati4 on 2014-02-03
Normally you would use the parallel port since it has buffered inputs, but you don't have one (I presume).  So you can use the Carrier Detect signal on a serial port:  [http://www.edaboard.com/thread75534.html](http://www.edaboard.com/thread75534.html).  Ignore the windows stuff, just find the equivalent serial port commands in linux.  For debounce and static electricity safety, the arduino is suggested as it will provide a buffer between your switches and the USB/serial port. 

You could use an old mouse and butcher it to get access to the switches.  Then you would assign the left and right clicks to perform functions.  The downside is that as a direct input on a headless server, you may not get any mouse input functions without an xserver running.

There must be some USB-based switches that you can interface.

Searching "usb interface switch"

[http://www.ablenetinc.com/Assistive-Technology/Computer-Access/Switch-Click-USB](http://www.ablenetinc.com/Assistive-Technology/Computer-Access/Switch-Click-USB)
[http://www.instructables.com/id/Mouse-Based-USB-Switch-Interface/](http://www.instructables.com/id/Mouse-Based-USB-Switch-Interface/)
[http://www.orin.com/access/swifty/](http://www.orin.com/access/swifty/)

If it was easy, then it would already be done.

---

### Post by Cookie Guru on 2014-02-03
> **tgalati4 said:**
> Normally you would use the parallel port since  it has buffered inputs, but you don't have one (I presume).You presumed correctly.> **tgalati4 said:**
> just find the equivalent serial port  commands in linuxAny suggestions there?  I'm language agnostic because I typically work with web languages, and they won't be of any help here.

---

### Post by tgalati4 on 2014-02-03
Well, then this link won't help either:  [http://en.wikibooks.org/wiki/Serial_Programming/Serial_Linux](http://en.wikibooks.org/wiki/Serial_Programming/Serial_Linux)

It might be easier to simply program a hotkey to an unused (or repurposed) multimedia key on your computer.

---

### Post by Cookie Guru on 2014-02-03
> **tgalati4 said:**
> It might be easier to simply program a hotkey to an unused (or repurposed) multimedia key on your computer.Agreed, but nobody is ever logged in locally.  So unless there's a way to listen at the login prompt it's going to have to be the serial or USB ports.

---

