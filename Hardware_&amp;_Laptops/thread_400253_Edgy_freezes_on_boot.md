---
title: "Edgy freezes on boot"
date: 2007-04-03
forum: Hardware &amp; Laptops
---

### Post by PryGuy on 2007-04-03
Good day everyone!
I've got a problem here: Edgy freezes during the boot stage. It appears during the HDD initialization I guess. The problem occurs in about 50% of all cases. His system dual boots with Windows XP SP2 and they share a 90Gb NTFS logical partition (Ubuntu uses NTFS3G driver, but I had this problem before I installed it). I've upgraded memory on his computer to 512Mb but I'm sure that the new memory module is okay, yet, his PC works fine under Windows.

I really do not know where to post this topic, but I'm sure it's not a software problem either 'cause I really had no problems with this PC before. Can MBR or partition errors cause such things?

His computer specs:
Motherboard: Foxconn 865 Series (can't say that is a good choice)
Video: Albatron FX5200
HDD: PATA Seagate 120Gb
Memory: 512Mb
Sound: Audiotrak Prodigy 7.1
PSU: 350W (Not sure about it's quality also, can it cause such problems?)

---

### Post by JNowka on 2007-04-03
If it was the powersupply you probably wouldn't get the thing to get to the loading screen.
If it was a mbr it would never boot, trust me, I have been there.
I would also guess a partition error also would prevent boot.

I would suggest trying to boot up in safe mode from the grub menu.  If that works I would guess that there are some improperly installed drivers somewhere.  I also found that my original wireless card's driver had a bug in it that caused the computer to just freeze in the middle of booting.  I had to download the driver and install it.  I have a "Intel Pro Wireless 3945AGB".  Hope this helps.

---

### Post by PryGuy on 2007-04-03
The thing that annoys me is that the problem does not occur all the time. Yet as far as I can remember this system used to run Edgy without problems and I didn't change anything except the memory module. And yes, I did a clean install for three or four times...

Yet, the nature of the bug seems to be very strange itself; working with computers I got used to eeh... certainty. But in this case system refuses to boot not always but sometimes only. When such things can happen speaking of computers?

---

### Post by smbm on 2007-04-06
> **PryGuy said:**
> The thing that annoys me is that the problem does not occur all the time. Yet as far as I can remember this system used to run Edgy without problems and I didn't change anything except the memory module. And yes, I did a clean install for three or four times...

Yet, the nature of the bug seems to be very strange itself; working with computers I got used to eeh... certainty. But in this case system refuses to boot not always but sometimes only. When such things can happen speaking of computers?


I'm no expert but this sounds like an intermittent hardware problem to me.

Good luck resolving it.

---

