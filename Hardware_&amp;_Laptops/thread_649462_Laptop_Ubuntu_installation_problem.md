---
title: "Laptop Ubuntu installation problem"
date: 2007-12-24
forum: Hardware &amp; Laptops
---

### Post by ducttapemasterJ on 2007-12-24
I am trying to put ubuntu on a Dell Inspiron 1000.  I dowloaded the ISO, and burned it as an image to DVD-R, restarted the laptop, and set the cd player as the boot priority.  When I turn on the laptop, it acts like there is no CD in the machine and boots windows normally.  the laptop won't even recognize the dvd.  However, I try putting the same instal dvd in the desktop and it boots into the ubuntu setup environmet.  I put another dvd inthe laptop and it plays just fine.  
Any ideas?

---

### Post by PaganHippie on 2007-12-25
Sounds like either the DVD drive in your laptop is faulty (does it read other discs OK?), or it's having trouble reading the DVD-R disc you burned.  If it's the latter, you may succeed by burning the ISO again to a different brand DVD-R disc (if you used, say, Memorex, try again with a disc from HP or another mfr).

---

### Post by Rocket2DMn on 2007-12-25
Did you download a dvd image file or is it just the cd image file?  If it's a cd image you need to burn it to a cd-r rather than a dvd-r.
You also need to check the md5sum of the image file (assuming CD right now):
[HowTo]("https://help.ubuntu.com/community/HowToMD5SUM")
[Hashes]("https://help.ubuntu.com/community/UbuntuHashes") to check against
You should also burn the disc at a slow speed like 4x to prevent write errors, and use quality media if possible.

If those fail, you may need to try the alternate install cd which doesn't have a live session - you can get it at [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and check the box for Alternate cd at the bottom.

If all that fails I would say it's a hardware problem (even though that other stuff works).  Then again, maybe the BIOS is just weird and won't actually boot from the dvd drive...

Hit us back with more details if you can.

---

