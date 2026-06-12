---
title: "serial port problems"
date: 2007-02-04
forum: Hardware &amp; Laptops
---

### Post by morganGDFP on 2007-02-04
I am new to ubuntu and to Linux as well and desperately need some help accesing the serial port.
i posted a thread yesterday regarding a simple parallel port problem and got that sorted out pretty quick so I thought I might as well post another one.

What I want to do is program an AVR Mega8 microcontroller using a stk500 kit via the serial port.

I have no idea how serial ports behave in ubuntu and how to access them..

I looked in the device manager and it would appear mine is called /dev/ttyS0..That is all i know about serial ports and ubuntu..
My questions would have to be something like this:

If I have a microcontroller that sends information on the serial port, how can I view that information on my PC?
Something like a terminal showing input from the serial port..
And how can I set baud rate and things like that?
And how can I send things on the serial port?

Thankful or reply
Morgan

---

### Post by RandomJoe on 2007-02-04
If you just need a basic terminal program, my preference is 'minicom'.  It's text-mode, so it runs in a terminal window.  I'm sure there are some GUI ones (one distro a while back had one called Seyon, IIRC) but minicom is pretty darn bulletproof so I haven't messed with others.  It acts a lot like Procomm/Procomm Plus of the DOS days, if you used that.

It isn't installed by default, of course - just install from Synaptic.  (Okay, just looked and the description in Synaptic says it's a clone of Telix.)

By default, it has modem strings set that it transmits on startup.  If your device might wig out getting random character strings sent on startup, you will want to change those before connecting up.

Edit:
Heh.  Just tried running it after fresh-installing, and it is for some reason defaulted to tty8 and won't run...  To start it straight into configuration mode, run 'minicom -s'.  You'll want to change the Serial Device to whatever your serial port is (probably /dev/ttyS0 as you mention).

---

### Post by morganGDFP on 2007-02-15
I thought i had posted a reply to this post ages ago, but apparently it never showed up...
Anyway, I tried minicom that you recommended and it looked like it would solve all my problems.
After a few hours of trying to get some output I however had to go elsewhere for a solution.
What I have is a microcontroller that outputs plain data (8 bits, no parity, 1 stop bit, no handshaking) and somehow I did not manage to get minicom to output this on screen.
I looked at avrfreaks.net and found a windows based terminal program that runs in linux under wine.

If anyone is interested it can be found here:
[http://bray.velenje.cx/avr/terminal/](http://bray.velenje.cx/avr/terminal/)

thanks for the help anyway.

---

