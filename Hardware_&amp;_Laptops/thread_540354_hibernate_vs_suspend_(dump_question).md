---
title: "hibernate vs suspend (dump question)"
date: 2007-09-01
forum: Hardware &amp; Laptops
---

### Post by OOzypal on 2007-09-01
I am sorry of it is trivial question but what is the difference btw hibernate and suspend?

---

### Post by nosmadar on 2007-09-01
When the pc is "hibernated", it is acually powered down.  BUT, it remembers the current state of the desktop.  any programs that were running are still in that state.  So you you power up a hibernating pc, don't have to login (if you were set up as a specific user) and all of the programs you had started are still running.

I don't suspend my PC much on purpose, but I think that's more like what happens when you leave it running long enough for the screen saver to start running and the power saving settings to take effect, so the HD may have spun down and the monitor could even have turned off.  BUT the pc is still technically powered ON.

At least thats how it works in XP, I haven't gotten that far with Ubuntu yet but I think these concepts are common to all portable PC hardware.

Hope this helps.
rob

---

### Post by nosrednaekim on 2007-09-01
hibernate is suspend to disk

suspend is suspend to ram. 

Suspend to RAM is faster (recovering and suspending) but if you lose power the suspend image is lost. suspend to ram also uses a minimal amount of power (less than a watt)

Suspend to Disk is slower, but you don't lose the image if you lose power. You can also have multiple OS's suspended to disk, since to select a image to resume you need to go through the GRUB menu.

---

