---
title: "ATI fglrx driver on Hardy 64"
date: 2008-12-12
forum: Hardware
---

### Post by Phasmagon on 2008-12-12
Hello everyone,

I have a problem that is bugging me for a while now.

A year ago I bought a Toshiba Satellite A210-16F

([http://eu.computers.toshiba-europe.com/innovation/product/Satellite-A210-16F/135223/](http://eu.computers.toshiba-europe.com/innovation/product/Satellite-A210-16F/135223/))

As every laptop sold in my country it had vista preloaded.
So after giving it a try to see what it can do I decided to do what I always do in the end. Flush vista and install ubuntu. So far so good. After resolving some minor issues wlan, bluetooth and 3D accelaration everything was rocking. Everything but one thing. Standby (and hibernation)

So this is the deal.

The computer goes to stand by and hibernates like a charm. But when it tries to wake up I get nothing. Just a blank screen. No desktop manager, no TTYs, not even ssh from another computer. It just stands there in a very dark mood.

After this happened a couple of times and I couldn't find anything on the net, I decided to reinstall vista to see what happens. So I popped in a spare drive and tested. Everything worked fine. At least nothing my warranty could help with.

The guess was that something was wrong with my ubuntu installation, but work did leave much room for playing around to find what was wrong.

So I forgot about it. Until recently when a friend came for help with an identical laptop running vista, which crashed during wake up.

To cut a long story short windows 32bit sleeps perfectly, windows 64bit crashes the driver (sometimes you get lines and triangles but you can shutdown and sometimes BSOD) and Hardy 64bit which is my flavor never wakes up, unless I don't use fglrx.

Everything points out to a driver issue.

So the question at hand is does anybody has the same problem with me.
And have you resolved it.

I would like to stand by my laptop, but much prefer 3D acceleration.

---

