---
title: "Battery Power Indicator - sporadic monitoring"
date: 2010-10-05
forum: Hardware
---

### Post by TheSiberian on 2010-10-05
I have a new Acer Aspire One 532h, on which I recently installed Ubuntu Netbook Edition 10.04

The monitoring of the battery levels seems to have some problems after restart. Sometimes after a restart, the OS thinks the battery is as critically low level, and proceeds to Suspend (when I know its at a fairly reasonable level)

After another restart, the monitor will then correctly show the battery level.

As such, in the Power Statistics - Device History I am seeing the normal & gradual decline of battery level, then after this issue, it takes a drop down to 0-2%. After another restart it spokes back up to where it should.

uname -a

```
Linux acer 2.6.32-25-generic #44-Ubuntu SMP Fri Sep 17 20:26:08 UTC 2010 i686 GNU/Linux
```Also (separate question), I want to disable the Wireless adaptor, however I seem to have to do this every time after a restart. Can I make this option stick, until I need to re-enable it?

---

### Post by g01d10x on 2010-10-06
I'm getting the same thing with my Battery indicator .. No idea what to do about it, but the battery life isn't there !!

I checked TOP to see if there were any unusually HUGE drains on the processor, and it seems that one processor core's load is usually around 100% .. not sure why this happens .. i'm used to Mac OS X .. which has a very low processor load if nothing is going on.

Anyone have any solutions ??

Acer 532h 10.04 Ubuntu

---

### Post by NightwishFan on 2010-10-21
Ubuntu is supposed to idle when not used, if not you'll need to identify what process is. Top/htop and powertop should help.

---

