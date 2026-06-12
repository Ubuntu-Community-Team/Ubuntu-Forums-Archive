---
title: "Ubuntu on Compaq Armada M300 PII"
date: 2007-06-15
forum: Hardware &amp; Laptops
---

### Post by EricWiz on 2007-06-15
Hello All,

I am trying to get this dinosaur of a laptop running with Ubuntu and I am running into a snag that I don't know how to troubleshoot.

I successfully got Ubuntu installed by using the alternate CD but anytime it boots the screen goes the color of the default background but I get no login screen. If I move the mouse around I get vertical lines on the screen but that is it. 

I thought this was a resolution issue so I booted to the recovery and went in and edited the xorg.conf to remove the 1024X768 resolution ( the screen maxes at 800x600). If, from the recovery console I then run startx I get the Gnome and I can login etc etc... BUT if I boot normally I get the  same issue as above. 

I am not sure how to diagnose this and I would really appreciate any help.

Thanks!
Eric

---

### Post by EricWiz on 2007-06-17
Bump.....

---

### Post by EricWiz on 2007-06-18
Found the issue. I guess I should chalk this up to RTFM. Ah well..

Anyway the issue was during the boot to add vga=771 and all worked well from there.

---

### Post by sanchrts on 2007-10-24
Dear EricWiz

I just noticed your post and was wondering if you could help a relative noobie with a similar issue.

I was running Ubuntu 7.04 perfectly on my Armada M300 500 Mhz PII and was using the machine as a web-browsing, distributed computing and BitTorrent platform.  Since there was no data on my install I did a clean install of 7.10 but have been experiencing extreme video "strangeness" including really messed up screens during install and then a vertical lines after install.

The specifications for the M300 are that it has an XGA display which I understand is 1024x768 and this resolution is what Ubuntu has defaulted to (Plug n Play monitor) so I don't know what the issue is but might try your solution - ***my question to you is*** - how do you set the VGA switch you suggested?

thanks in advance
Raf

---

