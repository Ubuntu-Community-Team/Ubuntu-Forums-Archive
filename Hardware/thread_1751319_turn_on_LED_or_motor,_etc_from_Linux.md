---
title: "turn on LED or motor, etc from Linux?"
date: 2011-05-06
forum: Hardware
---

### Post by mvmacd on 2011-05-06
I want to make a script so I can run a cron job to give power to some wires, outside my laptop. I know how to make BASH scripts, and have compiled some "hello world" C programs, but I have no idea how to tell Linux to give/cut power to a physical port [i.e. a USB port].
 
It would be very cool if I could switch the power on very very fast, to make a strobe light, and stuff like that.

How can I do this? I have a laptop, and thus no serial port.I **think** I have a USB-to-Serial port around here **somewhere,** but I don't know if i can find it... Is it possible to do with USB? :D

Thank you in advance!
Matt

---

### Post by grahammechanical on 2011-05-06
You would need something like this

[http://hacknmod.com/hack/top-40-arduino-projects-of-the-web/](http://hacknmod.com/hack/top-40-arduino-projects-of-the-web/)

Here is the home page for the ardino

[http://www.arduino.cc/](http://www.arduino.cc/)

I read about this little device in a Linux magazine. You can use Linux to program the IC.

Regards.

---

### Post by mvmacd on 2011-05-06
That looks neat.. Maybe I will look into buying one of them, if I can do cool enough stuff with it. :)

However... Is it impossible, to make a script turn on electricity going to some wires? Even with a serial port? I could always get another adapter on eBay.

---

### Post by tgalati4 on 2011-05-06
Typically you need a parallel port and some way to break out the connections to relays or switching transistors.  I have an old National Instruments Switching I/O board that does just that--it switches 16 channels on or off with simple C programs.  You can find them used on ebay.  For a modern solution, (like USB) then arduino is the way to go.  Any direct switching application is likely to fry your USB port and it's controller chip--which is likely shared with your network chip and memory controller.  So it's not a good idea to fool around with direct switching without going through some sort of interface.

---

