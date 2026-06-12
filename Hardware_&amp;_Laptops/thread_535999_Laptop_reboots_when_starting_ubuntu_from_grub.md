---
title: "Laptop reboots when starting ubuntu from grub"
date: 2007-08-27
forum: Hardware &amp; Laptops
---

### Post by bastiegast on 2007-08-27
I finally managed to install ubuntu(feisty server) on an old laptop. The laptop has 64 MB ram, and an 500 MHz AMD Processor. It fails to boot from a live cd(not enough RAM I suppose?) but I managed to install from a server install cd. The first time I tried it failed to install GRUB but the second time it mysteriously succeeded. 
When I rebooted my computer and selected ubuntu from the grub menu the screen flashes to loading ubuntu or something and then the laptop reboots!

This thread seems to be about the same problem:
[http://ubuntuforums.org/showthread.php?t=319275]("http://ubuntuforums.org/showthread.php?t=319275")

---

### Post by ddrichardson on 2007-08-27
64 Mb is a very small amount of RAM and to be honest the system itself may be running out of memory before the swap file is activated.

Try downloading [Damn Small Linux]("http://damnsmalllinux.org/") and running it - just to ensure there are no other problems. When you run it, specify the "noicons" option - I have even had problems with DSL on sub 128Mb machines.

---

### Post by bastiegast on 2007-08-27
Damn small linux is already installed on it and works like a charm :) (Without tweaking anything suprisingly) Even firefox 1.05 can run on it. I was just hoping to be able to run ubuntu on it.

Im going to hunt for some more memory, it shouldn't be very expensive for such an old laptop.

But still I don't think it's  the memory, I mean the installer loads a 2.6 kernel also doesn't it? So why doesn't even the kernel load?

---

### Post by ddrichardson on 2007-08-27
Well, in theory everything the installer does so should an install, but like I say  there may be a different order or service being loaded.

For small memory footprints, Xubuntu is better - more responsive. I have found Ubuntu will run (though through an alternate install) in 256Mb

---

