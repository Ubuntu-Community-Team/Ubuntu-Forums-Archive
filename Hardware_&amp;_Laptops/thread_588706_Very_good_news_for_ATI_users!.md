---
title: "Very good news for ATI users!"
date: 2007-10-23
forum: Hardware &amp; Laptops
---

### Post by mivo on 2007-10-23
[AMD 8.42 Driver Brings Fixes, AIGLX!]("http://www.phoronix.com/scan.php?page=article&item=887&num=1")

This should take care of most Compiz-Fusion issues that ATI users have in 7.10. :)

---

### Post by wolfjb on 2007-10-23
how soon will the 8.42 driver be available, my system still shows it running 8.37 (!) even after the gutsy upgrade

---

### Post by mivo on 2007-10-23
You can download it [here]("http://www2.ati.com/drivers/linux/ati-driver-installer-8.42.3-x86.x86_64.run"), but it may be better to wait a bit for [the backport]("https://bugs.launchpad.net/ubuntu/+source/fglrx-driver/+bug/156325").

---

### Post by grazzt on 2007-10-23
All I can say, is that I am hugely disappointed with this release.

Yes, I got AiGLX working, but man, so many things are so slow now.  Scrolling in firefox, movie playback, etcetc.

Good thing my card is R300 based, as the open source drive is not half bad (although no TVout)

Nice try ATI. :/

---

### Post by romana on 2007-10-23
My card is ATI Technologies Inc Radeon IGP 330M/340M/350M, and fglrx is borked completely for kernel 2.6.22 as far as other forum posts seem to indicate. ati driver working fine, but hangs occasionally, causing a cpu spike, less than a minute and back to normal.  and Neverwinter NIghts is my benchmark, not even attempting compiz until that runs smoothly. 

bring on the new driver!!!!!!!!!!!!!!!

---

### Post by drachenstern on 2007-10-24
My advice for you is to roll your own driver from the ATI provided bin

start here: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

The download link for the driver is in the text of the page, so no need to go digging.  Only bad part of that walkthrough was the having to reboot three times.  After that, I checked my xorg.conf and changed the 0 at the bottom to a 1 on this section:

Section "Extensions"
        Option          "Composite"     "1"
EndSection

Then I installed xserver-xgl and compiz is WUNDERBAR!

---

