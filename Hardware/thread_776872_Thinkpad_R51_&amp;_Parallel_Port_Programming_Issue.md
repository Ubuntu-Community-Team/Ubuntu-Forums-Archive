---
title: "Thinkpad R51 &amp; Parallel Port Programming Issue"
date: 2008-05-01
forum: Hardware
---

### Post by torf on 2008-05-01
A couple months ago, I started working on some basic parallel port programming on my Thinkpad R51 (port at 0x3bc) using the Parapin library ([http://parapin.sourceforge.net/](http://parapin.sourceforge.net/)). I got a few basic examples working which lit up LEDs connected to the parallel port (via a 74LS244), and planned to use this later on some microcontroller projects.

However, when I came back to the code a couple months later, it no longer functioned correctly. When I initialize the data pins as output pins with Parapin, they immediately go high, and seem to be locked that way. One of the programs I tested (which failed) was the outputtest.c provided as an example, with the port initialization changed from LPT1 to 0x3bc.
I verified that it was not a problem with the library by writing some quick and dirty parallel port code making an outb call - this yielded the same results. (Attempting to write 0x01 to the port resulted in 0x255 being written, and locked at that)

I've tried the exact same code, with the same parallel port adapter & circuit on another Ubuntu machine, which worked great.

Also, I've verified that the parallel port is not damaged by flipping some bits in Windows with a parallel port monitor. The circuit responded exactly as expected.

The only thing I can think of that has changed in these couple months are kernel and other updates. I'm just not too sure where to start on fixing this, and would appreciate any insight that could get me rolling in the right direction. I haven't seen any similar issues floating around on the net, so I would be curious to see if any other Thinkpad users encountered this issue. Below are just a couple details about my machine, please let me know if any other information would be of any help.

From dmesg:
[   17.852000] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[   19.344000] lp0: using parport0 (interrupt-driven).
[   25.140000] ppdev: user-space parallel port driver

uname -a:
Linux myhost 2.6.20-16-generic #2 SMP Tue Feb 12 05:41:34 UTC 2008 i686 GNU/Linux

Note: Also tried out 2.6.20-15-generic, issue persisted

gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4) - Parapin noted that you need to compile with -O, so just thought I'd include this.

---

### Post by chuni on 2012-06-09
replies 0  views 684

RUDE!!

I have the same issue with my t43 thinkpad.  I had it working at one point but i think i shorted some pins together and the port it screwed and everythings stuck high now.  Did you ever get this resolved?  I ended up using an even older laptop that has been working good for me.  Nice having a full 5 volts from the parallel port!

---

### Post by torf on 2012-06-10
> **chuni said:**
> replies 0  views 684

RUDE!!

I have the same issue with my t43 thinkpad.  I had it working at one point but i think i shorted some pins together and the port it screwed and everythings stuck high now.  Did you ever get this resolved?  I ended up using an even older laptop that has been working good for me.  Nice having a full 5 volts from the parallel port!

Not sure if you saw the date...this was May 2008! :P

I totally forgot that I was subscribed to this thread, let alone that I had this account! I can't recall if I resolved it or not. I'll assume not, as I would have posted back. However, I generally don't give up on stuff like this...so I wonder if it the problem when away with a later upgrade...

At any rate, I'll still try to give you hand. While I've since bought a Fujitsu latop, that Thinkpad R51 still runs. Maybe if I can get some free time, I'll hook up some basic stuff.

So let's start with some basic info about your setup, and go from there.
[LIST=1]
[*]What version of Ubuntu are you running?
[*]How are you interfacing with the parallel port? Perhaps you could share your code?
[*]Have you tried testing the issue in another OS? (For example, I either dual booted Windows XP, or swapped in an old harddrive).
[*]What's your parallel port hardware interface look like? I  would advise that you have some buffers between your parallel port and hardware to prevent damage to your laptop. (Take a look at 74LS240, 74LS241, and 74LS244 chips (or their 74HC* counterparts.) I know folks sometimes try to drive LEDs off their parallel port, but I'd much prefer to minimize any current I'd be sourcing/sinking to my laptop. Definitely buffer that I/O. Let me know if you want more details/links on this.
[/LIST]

---

