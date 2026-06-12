---
title: "Interesting Problem with Ge-Force FX 5200 Graphics Card"
date: 2007-04-05
forum: Hardware &amp; Laptops
---

### Post by gordyt on 2007-04-05
Howdy Folks,

Just wanted to share an interesting problem I had.  I recently put together a kit system from Tiger Direct that has a Mach Speed P4MSD-800D2 mother board, 2 GB RAM, and an Intel Pentium D 830 (dual core) processor.

Initially I had 64-bit Edgy installed.  I was having problems with the system restarting itself at random intervals.  Eventually I tracked the problem down to using the nvidia driver with the Ge-Force FX 5200 graphics card. 

If I disabled the nvidia driver, no problems, but of course less graphics performance.

I upgraded to 64-bit Feisty.  Same issues.

I swapped out that card with a GeForce 6200 LE that I had laying around.  Now the system works perfectly and no longer spontaneously restarts.  I used the spiffy new "Restricted Drivers Manager" tool to enable the NVIDIA accelerated graphics driver.

So you would think that maybe the FX 5200 card is bad, right?  But it works just fine in another (32-bit) system that I have.

Anyway, just wanted to pass that along as something to check if you have stability issues.

--gordy

---

