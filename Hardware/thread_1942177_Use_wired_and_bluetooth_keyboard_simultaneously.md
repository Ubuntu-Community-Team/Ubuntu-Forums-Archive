---
title: "Use wired and bluetooth keyboard simultaneously"
date: 2012-03-17
forum: Hardware
---

### Post by bakunin_yo on 2012-03-17
Greetings,

I'm trying to set up my system to have 2 keyboards connected- one to stay with my box in my office (ps/2 keyboard connector), the other to sit in my living room (bluetooth) where I have my computer hooked up to a projector.  I've found an interesting conflict caused by this set up.  The bluetooth won't stay connected as long as the wired keyboard stays connected to the machine.  I can connect it through the bluetooth manager and it works as long as I'm using it, but it "sleeps" after about 10 minutes and I have to reopen the manager and add it again, every time.  The interesting part is that as soon as the wired board is removed, I have instant signal and use of the bluetooth keyboard.

So, my question is whether anyone else has encountered this or has a similar set up where they've resolved the conflict.  I suppose I can deal with unplugging the wired board every time I want to use the bluetooth (or re-add the bluetooth keyboard after every time it gets dropped), but I'd prefer not...

System:
Ubuntu 10.04 LTS, 64-bit
Microsoft Bluetooth Mobile Keyboard 6000
IBM dumpster dived ps/2 keyboard

---

### Post by bakunin_yo on 2012-03-17
Actually, the bluetooth doesn't stay connected when the wired is disconnected...  So, any help with both problems?

---

### Post by bakunin_yo on 2012-03-18
Solved by following these instructions:

[http://www.thetechrepo.com/main-articles/520-how-to-connect-an-apple-bluetooth-keyboard-toubuntu-troubleshooting](http://www.thetechrepo.com/main-articles/520-how-to-connect-an-apple-bluetooth-keyboard-toubuntu-troubleshooting)

and

[http://ubuntuforums.org/showthread.php?p=9321724](http://ubuntuforums.org/showthread.php?p=9321724)

From the second link (second post down), all I did was remove the hash from the time out line and set the timeout= 0 in /etc/bluetooth/input.conf

I hope this helps someone else down the line. :D

---

