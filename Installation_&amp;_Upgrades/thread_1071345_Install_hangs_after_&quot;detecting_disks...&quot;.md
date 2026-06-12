---
title: "Install hangs after &quot;detecting disks...&quot;"
date: 2009-02-16
forum: Installation &amp; Upgrades
---

### Post by NeoDevin on 2009-02-16
I'm trying to install Ubuntu (preferably server, but anything is better than nothing) on an old machine I have here (very old, 667MHz processor, 64MB SDRAM).  and I have the same problem with both the server, and the alternate install disks.  In the alternate install, I choose the "text only" option, and then try to install.

I tell it not to set up the network with DHCP when it asks about that (will set that up later), and after a bit it goes to "detecting disks and all other hardware", the progress bar fills to 100%, the screen blinks and it's back at 0%, it blinks a few more times, each time coming back at 0% again (only the first time does it actually say anything other than 0%, after that it just blinks off and on 0%).  After a while of that, it just goes black, with a white bar at the bottom of the screen, and blinks regularly.  After a while of that, the screen goes black, and has been repeatedly printing the word "killed" ever since.  If anyone has any advice on what I should do differently, I would appreciate it.

Thanks in advance.

Devin

Edit:  The exact same thing happens with the server install disk, though I didn't wait long enough for it to start printing "killed".

Edit 2: It's an HP Pavilion 6736, if that helps.

---

### Post by lisati on 2009-04-04
I've had a similar experience with a Digital Venturis, Pentium, 133 MHz, 64Mb RAM, 3Gb HDD: it manages to configure the network with DHVP and then gets into what looks like a loop stuck at 0% detecting disks and other hardware. It could be that the "regular" install won't work on our machines, even with the alternate CD

---

