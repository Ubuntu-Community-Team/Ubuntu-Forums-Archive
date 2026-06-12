---
title: "Kernel Panic on resume from suspend (S3) - Zepto Nox A14"
date: 2009-06-09
forum: Hardware
---

### Post by Taijitu on 2009-06-09
Hello you wonderful community :-)

I have now searched across the web for an entire day for something that might rid me of this problem.

I got a wonderful new laptop yesterday, the Zepto Nox A14, on which I am running Jaunty 64 bit.
However, it refuses to resume from suspend/standby. no problem with hibernate

It suspends seemingly without problems, but when I turn it back on, screen continues to be off and HDD indicator is as well, indicating that it is not just the screen that doesn't turn on. However, Caps lock and Scroll lock are flashing... Indicating Kernel Panic.

I tried removing the Nvidia drivers, but that did not help.

I'm sure this could be solved by dissecting dmesg output and the alike, but I am not experienced enough in this area, so I was hoping someone in here could help me solving this problem.

In advance, Thank you.
And may you have a good day.

Christoffer

---

### Post by blueglow on 2009-07-28
Me too; suspends fine, no resume on 64bit Jaunty with 2.6.28-13-generic kernel, nVidia GTX275 with their restricted driver, Core i7 on Asus p6t se, Edimax wifi card.

Can't see anything useful in the logs, though the fragment of Syslog attached shows the computer suspending then ignoring me mashing the keys until I hit the power button, at which point it starts to come back to life then kernel panic sets in and I hit the reset button.

There's a LOT of bugs over at launchpad related to this, and none seem to go anywhere or shed much light.

If anyone knows any logs/commands/ideas as to how I can shed more light on this, that'd be great!

---

### Post by Taijitu on 2009-07-28
Actually, I think my issue is more hardware-related than Linux-related, as I've heard that it's the same issue with my Laptop model when it's running Windows XP (as opposed to Vista/7)... So... I guess I can hope for a BIOS update that fixes it or some magic happening to the Linux Kernel... Luckily Jaunty doesn't take a very long time to boot, so I can live without S3 for now...

---

