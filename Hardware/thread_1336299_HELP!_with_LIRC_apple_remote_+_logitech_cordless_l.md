---
title: "HELP! with LIRC apple remote + logitech cordless laser"
date: 2009-11-24
forum: Hardware
---

### Post by maxxerific on 2009-11-24
hi all - 
  i'm having a darn hard time setting up LIRC.
1st off i'm not even sure if what i'm trying to do is possible.

i bought a logitech cordless laser (lsusb shows it as "Logitech, Inc. LX710 Cordless Desktop Laser")
And i'm trying to get it to receive commands from my Apple remote (came with my macbook pro. NB: i'm trying to use the remote on a generic PC with ubuntu 9.10)

running the GUI for infrared remote control was detecting a logitech receiver. but now it only sees 'linux input device power button and sleep button'.

any advice?

best 
maxx

---

### Post by maxxerific on 2009-12-04
The LIRC mailing list helped me on this one:

short answer: not possible.

---

### Post by permagnus on 2009-12-29
Why did it not work?

---

### Post by maxxerific on 2009-12-29
this was the answer i got: 

"Pretty sure what you're trying to do isn't possible. That's not a general-purpose IR receiver, its a receiver for the matching keyboard and mouse. It does onboard decoding of the expected signals from the keyboard and mouse only. Now, if you had a learning universal remote, you might be able to teach it keystrokes from the keyboard, and send those to the receiver. But yeah, the apple remote is a non-starter."


maybe not difninitve but solid enough for me not waste any more time :) 
my advice would be to buy one of the (proven + cheap) options of IR devices rather than to mess about with two propriteary devices.

---

