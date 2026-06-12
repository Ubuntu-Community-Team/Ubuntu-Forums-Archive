---
title: "Various Problems"
date: 2005-10-17
forum: Hardware &amp; Laptops
---

### Post by Corvus on 2005-10-17
I had problems with different devices.

I have a BenQ DW1640 DL unit. It's a dvd rewritable unit. I have problems with it in the past because when installing, dma wasn't activated so i had to enter in the expert mode and pass the 'dma = on' parameter for hdaparm or install it with an old cd-rom unit. That fixed the problem and i could install the os.

Actually i tried breezy, i wanted a clean install instead upgrading hoary, so i tried again with my dvd unit. Now i couldn't do nothing because after loading vmlinuz, it showed me this error and i needed to reboot the computer:

'isolinux: Disk error 80, AX = 4261, drive 9F'

Then i tried with the old cd-rom unit i had. It started very well installing everything. But it always failed when installed one of the packages. As it is an old unit maybe he starts to fail so, i don't care too much for this old cd-rom. At last i had an old sony cd-rw unit, and the os installed well with it.

The other problem is with a joypad i have. A usb Saitek P750. It never worked with ubuntu. It has a red led to show that it is connected to the computer and power arrives to it. Since warty, that led was on but the joypad didn't work. Since breezy, it sometimes is off and the joypad is still not working.

I use the computer mainly for work, so i don't care too much. But it would be nice to see it working again.

I don't know what to do with these two. Fill a bug in bugzilla, or let them here ?

Thank you,

---

### Post by DevilGuy on 2006-02-22
You know, I get the same error on a similiar DVD drive.  I have a Sony DRU-810A, which I have read it is exactly the same as your BenQ DW1640 with the Sony name outside.

Not only do I get this error message when I try to install Breeze, but also when I try to boot up from a Knoppix distro I downloaded last week.   I'm starting to think this problem might be an issue with this drive (or it could be a coincidence).

Initially I thought the Knoppix dvd I burned was bad, but when I try it on my laptop, it boots up without any problems.  I wonder if anyone else might be having this same issue!

---

### Post by infoseeker on 2006-02-22
Read the posts in these threads:

[http://www.ubuntuforums.org/showthread.php?t=107529&highlight=dw1640](http://www.ubuntuforums.org/showthread.php?t=107529&highlight=dw1640)

[http://www.ubuntuforums.org/showthread.php?t=72056&highlight=dw1640](http://www.ubuntuforums.org/showthread.php?t=72056&highlight=dw1640)

---

### Post by robaroooo on 2006-04-16
I had a similar problem on first attempt installing breezy and tried two different cd/rw drives with same message at isolinux... error 80, etc. After blowing several hours troubleshooting, I decided to download a new copy of ubuntu and happened to use truedownloader. Don't know if that matters. Anyway, burned it on to a different disk and it started just fine. Now I haven't finished the install yet, I just got excited to make it past the starting line. Hope all this works. My aim is to use Ubuntu with MythTV! Hope this helps anybody out there.

---

### Post by dnel83 on 2006-06-03
I had this same problem with Dapper on my Sony DRU-810a it gave that error booting from the live CD which I burned to two different discs and also the live DVD. 

I fixed it by upgrading the DVD drive's firmware from 1.0a to 1.0e. There might also be a firmware upgrade available for the BenQ drive which will help you.

HTH

---

### Post by isenalim on 2006-06-26
I had a booting problem with the dapper CD similar to yours.

I upgraded the firmware of my DVD drive Philips DVDR1648P1 to the 2.3 version and now it seems to work!
I'm checking the cd now, and all seems ok!

Hope similar thing will work for you!

Bye
B

---

