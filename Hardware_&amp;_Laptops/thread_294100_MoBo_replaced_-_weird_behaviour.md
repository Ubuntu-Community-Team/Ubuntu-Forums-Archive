---
title: "MoBo replaced - weird behaviour"
date: 2006-11-06
forum: Hardware &amp; Laptops
---

### Post by DFreeze on 2006-11-06
I’ve recently replaced a flaky and dying motherboard with a new AsRock K7NF2-RAID. Ubuntu didn’t even blink! Ain’t that grand…

On the other hand, there is some hardware / memory related stuff I can’t get going right. The symptoms are weird (in my perspective). Maybe one of you has a clue as to what’s going on.

Right from the start, the system feels extremely slow. Memory check, IDE scanning, take much longer than they have to. When entering BIOS, the board has a nice gradient scrolling title bar, but the scrolling is stuttering. It moves for about half a second and freezes for the next one second. The system is completely numb when in freeze. No reaction to my keyboard whatsoever. 
I’ve tried some alternating memory timings (relaxing the auto-settings a bit), but to no avail. 

The strange thing is, this stuttering (0.5 seconds of work, 1 second stall) can even be seen in the throbber when booting. Once the OS shows, however, I can work fine. The system monitor does not show stalls, the system is responsive and it looks like there’s nothing going on. 

Booting from the liveCD (Edgy) also shows stuttering startup and boot, but not a slow desktop. What on earth is going on here? Does this sound familiar to anyone?

AMD XP-2100+
AsRock K7NF2-RAID
2x 256 MB DDR400 (Elixir), 1x 256 MB DDR333 (PQI) (used as DDR266)
GeForce4 MX440 64MB

---

### Post by DFreeze on 2006-11-08
Ok, here's an update on the situation. Booting into BIOS with all the IDE cables unplugged does not fix it. The stuttering is actually more annoying than suggested above. I have to wait some 2 or 3 seconds before getting another 0.5 second window of activity...

Does anyone here have some hardware-intuition that can indicate where to look? Or does it sound like the board is faulty and should I get a replacement?

---

### Post by DFreeze on 2006-11-10
Again an update: since yesterday the system fails to boot entirely. No beeps, no video, nothing... I only reinserted the two sticks of RAM because the problem wasn't solved using just one.
Removing the RAM again didn't revert the situation, so now I'm left with a dead system. I'm going to give it one more look but it looks like an RMA to me.

---

### Post by DFreeze on 2007-02-22
An update: 

I've not been able to use the system, because the shop I RMA'd the MoBo to didn't send it back, didn't reply to any requests, and in the end I found out why: they went bankrupt...

So, money gone, and no motherboard. I found a two-year-old Asus a7n8x-deluxe secondhand and installed it. More than two months I've been fighting with this computer, but the Asus fixed it all. 

No reinstalls, all hardware working. I only needed to do 'sudo dpkg-reconfigure xserver-xorg' to fix X. 

So: resolved!

---

