---
title: "Should I be worried about my hardware not working properly?"
date: 2010-08-23
forum: Hardware
---

### Post by darkestfright on 2010-08-23
Hi,

been an Ubuntu/Linux user ever since 6.06.  Never really had any issues with hardware or so I thought.  After years of using Ubuntu, I finally discovered the `lshw` command.  Here's where the problems come in.  Whenever I've used Ubuntu, all of the hardware that I could 'see' has always worked.  Things such as wireless, graphics, ethernet, usb devices have always worked like a dream.

When I took a look at the output of `lshw -html > hw.html`, I became a little unerved.  There were a few pieces of hardware that were highlighted in red, I looked this up on the lshw website and they say that it's because their is no kernel module(driver) loaded for that particular piece of hardware.
These are the entries here:

[HTML]
id:	
communication
description:	Communication controller
product:	5 Series/3400 Series Chipset HECI Controller
vendor:	Intel Corporation
physical id:	
16
bus info:	
pci@0000:00:16.0
version:	06
width:	64 bits
clock:	33MHz
capabilities:	pm msi bus_master cap_list
configuration:	
latency	=	0
resources:	
memory	:	fbbffc00-fbbffc0f

id:	
serial
description:	SMBus
product:	5 Series/3400 Series Chipset SMBus Controller
vendor:	Intel Corporation
physical id:	
1f.3
bus info:	
pci@0000:00:1f.3
version:	06
width:	64 bits
clock:	33MHz
configuration:	
latency	=	0
resources:	
memory	:	fbbff800-fbbff8ff
ioport	:	400(size=32)

id:	
power
description:	To Be Filled By O.E.M.
product:	To Be Filled By O.E.M.
vendor:	To Be Filled By O.E.M.
physical id:	
1
version:	To Be Filled By O.E.M.
serial:	To Be Filled By O.E.M.
capacity:	32768mWh[/HTML]

Notice that one of them is my system's PSU.  I don't even know what the other 2 things are...so after some quick searching on Intel's site, I've read that an SMBus controller monitors the voltage and temperature of the motherboard, and the HECI controller...well...I have no clue after reading this:

[http://software.intel.com/en-us/blogs/2007/01/24/let-us-talk-about-heci-and-lms/](http://software.intel.com/en-us/blogs/2007/01/24/let-us-talk-about-heci-and-lms/)

This is extremely unerving to me, these seem as pretty important things to need drivers for...
Then again, I'm no hardware expert, and have no idea how Linux handles hardware it doesn't have drivers for so any more educated input is appreciated.  Thanks

---

### Post by darkestfright on 2010-08-23
That's not an issue, I have more than enough ram and a decent video card for what I use the computer for.

My concern is that because there are no drivers for these particular hardwares that it will cause physical damage to the hardware because of lack of power management or other things.

---

### Post by darkestfright on 2010-08-24
Nobody else has any input?

Is it possible that lshw gives false negatives?  I've had an ethernet port show up as 'unclaimed' on my laptop but it works just fine.

---

