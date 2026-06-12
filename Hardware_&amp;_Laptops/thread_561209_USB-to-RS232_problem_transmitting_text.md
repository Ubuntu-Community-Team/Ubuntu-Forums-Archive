---
title: "USB-to-RS232 problem transmitting text"
date: 2007-09-27
forum: Hardware &amp; Laptops
---

### Post by kofileblanc on 2007-09-27
Equipment:
Hardware: 1. usb-to-rs232 cable (PL2303H) 2. 68hc11 microcontroller
Software: 1. ubuntu running ckermit (or minicom)

What works:
1. When I manually reset the microcontroller it sends its prompt - "BUFFALO 3.4 (ext) - Bit User Fast Friendly Aid to Logical Operation"
Which means:
1. Receive (Rx) is working
2. The speed is configured correctly
3. No other hardware issues

What doesn't work:
1. When I send text commands I get no response from the microcontroller.
2. File transmission
Behavior:
1. At the connection window the blinking prompt goes blank momentarily but no character appears (The character echo is handle by the controller, so typing characters will appear at the prompt)
2. The microcontroller's LED indicating transmission is not receiving a signal

Noticeable behaviour:
1. I've successfully been able to communicate with the microcontroller using a MAC OS X laptop. (Using the same cable running kermit)
2. When I restart ckermit in Ubuntu, I notice that it sends a command to the microcontroller. For instance, if i were attempting to see a memory dump of the contents of the microcontroller I would type: md 1400
    When i restart ckermit, this command would be sent to the microcontroller. (Perhaps the cable is clearing out it's buffer)

... Well that's it. Thanks for reading this far. Hopefully my problem is easily solvable.

---

