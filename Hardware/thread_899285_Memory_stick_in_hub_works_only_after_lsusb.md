---
title: "Memory stick in hub works only after lsusb"
date: 2008-08-24
forum: Hardware
---

### Post by RainKap on 2008-08-24
This isn't a critical problem, though it had me tearing out my (thinning) hair for several hours...

I recently bought a Belkin F5U261 4-port internal USB 2.0 hub to put in my Linux box, to give me front panel access to plug in a memory stick. At first I thought I had a hardware problem, but by plugging it into my Windoze box I found it was working OK. Symptoms were that a USB membory stick, which works fine in the back panel ports (and in the motherboard port to which the hub is connected) wasn't automounted when I plugged it into one of the hub's front panel sockets. I tried doing lsusb from a terminal, and the hub is recognised as a Belkin device with ID 050d:0261. Only if I do lsusb *after* I plugged in the memory stick does the system mount the memory stick.

lspci shows the USB controller as an nVidia MCP55 (one of two).

I'd rather not go down the road of disabling USB 2.0, because I sometimes want to shovel big files between the HD and the memory stick.

Any suggestions for how to iron out this wrinkle would be gratefully received.

Ian

---

### Post by RainKap on 2008-08-28
An update: I found that the same symptom applies to the USB floppy which I've plugged into the USB hub.

*However*, if a device is plugged into the USB hub when I start the machine, it's recognised without the need to jump through the lsusb hoop...

Curiouser and curiouser...

Ian

---

### Post by Thanh-BKK on 2008-10-17
Hello :)

Sadly i do not have an answer or a solution, but i am facing the exact same problem, since today! 

As i had a different problem with USB sticks (horribly slow transfer speed) and read that a new kernel will have it fixed, so i finally decided to DO the kernel update (which i had refused before as my machine was running perfectly with the old, Hardy-first-release, kernel.

Now, with the new kernel (and a shipload other updates) my USB stick also won't mount when i plug it in, but it DOES mount after i do the "lsusb" command.

And yes, i did not mention this in my own thread about the subject, the USB stick is indeed in a hub, too (external, hooked up to one of the mainboard connectors in the back of the PC). 

I, too, would appreciate a solution to this issue.

Kind regards.....

Thanh

---

### Post by dcook32p on 2008-10-18
I, too, have this problem. I have a USB hub integrated into my Dell 1907Fpv LCD monitor. During the installation from the 8.04.1 Live CD, my 256 MB USB flash drive showed up in the list of volumes.

However, once I updated to the latest kernel (I did not think to look before the updates), I can no longer get it to recognize from this hub without first running lsusb.

Suggestions?

---

### Post by oset on 2008-10-22
Same goes for me. Using an external 4-port Cypress based hub. Worked flawless before upgrade yesterday to 2.6.24-21. It might be hal related. Running lshal -m there is no sign whatsoever when memory stick inserted. Issue an lsusb in another terminal and voila the memory stick is detected. Using a "normal" (direct to motherboard) USB port works perfect. Seems like the hub is "disconnected" after use. Bug or configuration change?! Not critical but quite annoying when you try to convince "non Linux powerusers" to convert to Linux, ;)

---

### Post by Blackwood on 2008-11-21
It would appear this is a common error.  I have the same problem.

Running Ubuntu 8.04.1, kernel 2.6.24-21-generic.

Does anyone know if this has been logged as a bug anywhere?  Is there a solution?  It's just extremely annoying to have to run lsusb every time I plug in a USB device.

---

### Post by Thanh-BKK on 2008-11-21
Hi :)

Yes i filed it as a bug on launchpad. Meantime i found out it applies only to 2.0 hubs, i.e. when i use a USB 1.1 hub the devices ARE detected the instant they are plugged in, but not so on USB 2.0 hubs.

And i tried a whole bunch of hubs.

Kind regards....

Thanh

---

### Post by Blackwood on 2008-11-24
Thanks Thanh-BKK!  Can you post the bug number, or at least keep this post updated with any news?

---

### Post by Thanh-BKK on 2008-11-24
Hi :)

Sure, here's a link: [https://bugs.launchpad.net/ubuntu/+bug/285006](https://bugs.launchpad.net/ubuntu/+bug/285006)

With kind regards....

Thanh

---

### Post by RainKap on 2009-06-05
An update on this: now I've updated to Jaunty, the problem has gone away, and USB devices plugged into the hub are recognised immediately, with no need to use lsusb.

Ian

---

### Post by Thanh-BKK on 2009-06-05
Hi :)

I'm still on Hardy but for me it has gone away as well - after updating my hardware, i.e. mainboard and CPU! 

Now for me, too, the USB stick is automatically detected again despite being in the hub (and that hub, like before, plugged into one of the rear USB connectors). 

Kind regards.....

Thanh

---

