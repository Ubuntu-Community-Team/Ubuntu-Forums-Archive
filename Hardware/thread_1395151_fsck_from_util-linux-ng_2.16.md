---
title: "fsck from util-linux-ng 2.16"
date: 2010-01-31
forum: Hardware
---

### Post by fenrisW0lf on 2010-01-31
Hi all,

I have an emachine e250 netbook (very similar to acer aspire one) that I installed Ubuntu netbook remix (karmic) on yesterday. I had some problems with the wifi card yesterday but I managed to get everything working fine. This morning when I went to boot up the netbook wouldn't boot past the little circle logo in the center of the screen.

Restarting the laptop (holding the power button in for a hard reboot) and then choosing the recovery console in grub I noticed that the last line that would be executed was "fsck from util-linux-ng 2.16" before the machine froze with no activity. 

I can boot from the usb key that has the ubuntu netbook remix live-cd installed on with out a problem and the netbook works great.

I suspect that it has something to do with ntfs recovery partition at /dev/sda1. 

Any ideas or advice?

---

### Post by fenrisW0lf on 2010-02-01
I ended up reinstalling Ubuntu netbook remix (formatted the root partition). It seems to boot ok now. It was probably my fault when I got the wireless network card running. I am not sure what I did, but sometimes it seemed to stop at a message indicating that the wireless network card was causing problems.

---

