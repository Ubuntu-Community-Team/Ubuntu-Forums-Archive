---
title: "gutsy: Dell Latitude 820 locks up if suspended overnight"
date: 2007-12-13
forum: Hardware &amp; Laptops
---

### Post by Niels Olson on 2007-12-13
Dell Latitude 820 keyboard doesn't seem to respond if I suspend at night and wake it up the next morning. Suspend otherwise seems to work. I can close the lid, it suspends to ram, and when I open the lid, it wakes back up. I have to recycle the Broadcom 43xx wireless card, but otherwise, it works. Problem is, it's my wife's laptop. I'll go over everything in the evenning, demonstrate that suspend and wake work, suspend it before going to bed, and when she takes it to work the next morning and wakes it up, the screen comes up, but the keyboard appears to be unresponsive. So she reboots into Windows. I believe her exact quote the last time was "You know the problem with Linux? I like it, but it just doesn't work."

---

### Post by bluedragon436 on 2007-12-14
I can't seem to get my suspend/hibernate to work at all, if I close the screen and open it back up I get a blinking cursor on a blank black screen, and have to restart...if I leave it overnight I have to cold boot it...so at least you can get yours to come back out of suspend....  it is all a matter of time and they will find a fix for it...

---

### Post by Niels Olson on 2007-12-14
> **bluedragon436 said:**
> I can't seem to get my suspend/hibernate to work at all, if I close the screen and open it back up I get a blinking cursor on a blank black screen, and have to restart...if I leave it overnight I have to cold boot it...so at least you can get yours to come back out of suspend....  it is all a matter of time and they will find a fix for it...

Have you tried changing POST-VIDEO to "False" in /etc/default/acpi-support?

My problem only seems to happen when the suspend goes overnight. The keyboard locks up and the only button that seems to work is the power button.

Edit 4 May 08: suspend-to-ram overnight seems to work in Hardy Heron.

---

