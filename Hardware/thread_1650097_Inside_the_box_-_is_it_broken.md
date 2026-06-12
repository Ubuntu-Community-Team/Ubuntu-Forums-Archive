---
title: "Inside the box - is it broken?"
date: 2010-12-21
forum: Hardware
---

### Post by AmpersUK on 2010-12-21
I ran **sudo lshw -html > hw.htm** to note the contents of my 64-bit box and one item was printed in red when I viewed hw.htm

This is the offending item:

id: serial
description: SMBus
product: SBx00 SMBus Controller
vendor: ATI Technologies Inc
physical id: 14
bus info: pci@0000:00:14.0
version: 3c
width: 32 bits
clock: 66MHz
capabilities: ht cap_list
configuration: 
latency = 0

I am surmising that 

(a) this item is not functioning properly
or
(b) this is the wrong item for a 64-bit box

As my computer performs excellently, I gather that this is not really needed.

Before I contact my supplier I would like to know that I have come to the right conclusion?
[B]
QUESTION[/B]
Could anyone tell me what this really means?

---

### Post by IcarusR on 2010-12-21
I have just run the same command & get the same item in red.
The id is serial, my laptop does not have any serial ports so none are configured & it is not in use.

Is serial port disabled  in your bios ?

---

### Post by AmpersUK on 2010-12-21
> **IcarusR said:**
> I have just run the same command & get the same item in red.
The id is serial, my laptop does not have any serial ports so none are configured & it is not in use.

Is serial port disabled  in your bios ?

Not sure how to find out, but I suspect it might be. I also don't use a serial port on my desktop so I will let it rest.

Thanks for your detailed reply as the first part indicates I need not worry :-)

---

### Post by IcarusR on 2010-12-21
When booting up press delete gets one to bios settings on some mobos, others it is f10 or f12. Read in your mobo/box manual.
Once in bios there should be a page where hardware can be enabled/disabled & setup.
But as you say if you don't use serial port it is not much to bother about.

---

### Post by AmpersUK on 2010-12-21
> **IcarusR said:**
> When booting up press delete gets one to bios settings on some mobos, others it is f10 or f12. Read in your mobo/box manual.
Once in bios there should be a page where hardware can be enabled/disabled & setup.
But as you say if you don't use serial port it is not much to bother about.

I found the item, there is one serial port listed with [3F8/IRQ4] set against it.

But it's not too important as it is one year old and I usually upgrade in two to three years.

Thanks a lot for your help, it is much appreciated.

---

### Post by Fafler on 2010-12-21
SMBus =! RS232

It's a completely different kind of serial port. The SMBus is used for reading hardware info, like temperature and memory timings. Or if you have a ATI graphics card, it's probably used for reading EDID data from your monitor.

Install and use the sensors package to try it out.

---

### Post by AmpersUK on 2010-12-22
> **Fafler said:**
> SMBus =! RS232

It's a completely different kind of serial port. The SMBus is used for reading hardware info, like temperature and memory timings. Or if you have a ATI graphics card, it's probably used for reading EDID data from your monitor.

Install and use the sensors package to try it out.

Can't find a package called sensor so I will leave it. Thanks anyway.

BTW you have my permission to say it :-)

Ampers.

---

