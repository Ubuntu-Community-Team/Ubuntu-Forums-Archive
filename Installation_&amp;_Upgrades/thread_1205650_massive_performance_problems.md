---
title: "massive performance problems"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by aLiEnTxC on 2009-07-06
Hi Guys,

my Ubuntu installation 9.04 and before the "Intrepid Ibex" have massive performance problems. I get them most, when I use programs, that massively use my harddisk, e.g. vmware or copy/move from SD-Card-Reader to harddisk...

The system is during this time not able to response, or mouse movement hangs and stutters around - for me it is not usable :evil:

My System infos:

[http://paste.ubuntuusers.de/395732/](http://paste.ubuntuusers.de/395732/)

I need help, what can I do?

Regards,
Thomas

---

### Post by Mark Phelps on 2009-07-07
You didn't say anything about performance problems when NOT using either a virtual machine or a card reader, so I'm presuming that the system response is OK then.

As you probably know, any VM is going to perform slower than a native OS, and is critically dependent on the amount of system memory allocated to it.

You didn't mention how much of your system memory you have allocated to the virtual machine, nor did you mention which OS you have running in the virtual machine.  If, for example, you're running Vista in the VM, and you only have 1GB of your memory allocated to it, I would expect all VM operations to be painfully slow.  My own experience with Vista is that it doesn't become reasonably performent until you have 2GB of memory available.

Also, the VM is going through interface layers to get to the devices, so again, any disk/card activity is likely to be a low slower than using a native OS.

Other than allocating more memory to the VM, don't know what else to suggest.

---

### Post by aLiEnTxC on 2009-07-08
It is not a vmware problem, same vm under older linux or windows host running very fine. I also have the problem without vmware.. by only copy files under Ubuntu from a SD-Card to my Harddisk.

I think the problem is on the kernel scheduler, which give hardware IO from my harddisk more prio.. 

On older linux systems my X-Display was never so bad in response like now.

But i'm not sure and also don't now how to inspect it correct.

---

### Post by aLiEnTxC on 2009-07-15
hi.. 

I installed today kernel-image-2.6.31-3-generic and now it is mush better - but not perfect.. but now I can start vmware without system slow down to 1% :guitar:

---

