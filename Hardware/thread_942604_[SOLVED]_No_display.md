---
title: "[SOLVED] No display"
date: 2008-10-09
forum: Hardware
---

### Post by lost09 on 2008-10-09
I've just reinstalled (Gutsy, as it was the only CD I had available) after a cataclysmic system failure. I'm able to get the characteristic start-up sound, and I know I can log in... problem is: the monitor is completely black. Will a second reinstallation fix this problem, or does this represent an impossibly more annoying error?

n.b. There were no display problems prior to the system crash, nor with the live CD.

Thanks,
l

---

### Post by biggyfred on 2008-10-09
What kind of monitor? What video card? What kind of connection from video card to monitor?

---

### Post by lost09 on 2008-10-09
The monitor is that of a 3+ year old Toshiba Satellite with, I believe, an ATI Radeon graphics card.

---

### Post by lost09 on 2008-10-09
There is no physical problem with the monitor, as it functions perfectly during bios and live CD.

Anyone? Please??

---

### Post by lost09 on 2008-10-10
Do I have any options shy of physical replacement?

---

### Post by overdrank on 2008-10-10
> **lost09 said:**
> Do I have any options shy of physical replacement?

Can you reach the terminal, using the keys ctrl, alt, F1?

---

### Post by lost09 on 2008-10-10
I've yet to try. What do I type-in if I'm able to reach it?

---

### Post by overdrank on 2008-10-10
> **lost09 said:**
> I've yet to try. What do I type-in if I'm able to reach it?

You may try and reconfigure you xorg. ```
sudo dpkg-reconfigure xserver-xorg
```
Then you may reboot with ```
sudo reboot
``` Hopefully this will correct the issue.

---

### Post by lost09 on 2008-10-12
I tried that, to no avail. Actually, it seems to have made things worse, as now I can no longer get into the terminal.

I had a Suse disc on-hand, and out of desperation installed that. It seems to be working (minus wireless, and a disturbing absence of g++), so I think the problem lies with the Ubuntu disc rather than with my hard-drive.

---

### Post by lost09 on 2008-10-13
As the problem seems to lie with the disk and not with Ubuntu or, as I had previously suspected, with my computer, I have marked this thread as "solved". Thanks to all for your assistance.

---

