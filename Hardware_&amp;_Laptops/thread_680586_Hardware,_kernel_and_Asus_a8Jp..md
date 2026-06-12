---
title: "Hardware, kernel and Asus a8Jp."
date: 2008-01-28
forum: Hardware &amp; Laptops
---

### Post by UbLove on 2008-01-28
Hello.

I have some problems with my A8Jp. 
1) In "generic" kernel (2.6.22) Ubuntu 7.10 -  hibernate/suspend to ram/disk doesn't work.
2) In 2.6.23 + 14 patch i can't make iwlwifi - errors "incompatible module format". mac80211 - compile and work, iwl3945 - doesn't.  In 2.6.22 (from source deb) it's work well with same sources !!!
3) In my patched 2.6.22 kernel (lnux-phc , uvesafb + v86d, tuxonice ) all ok, except hibernate ! Cartreader, ati x1700 (compiz), webcam, sound, CPU + voltage, WiFi -all work well, but no suspend/hibernate :(
P.S. Unload modures like "modprobe -r iwl3945" not work for me :(

Thanks for the HELP!!

---

### Post by UbLove on 2008-01-28
In gentoo forum the same problems with iwl3945. "Invalid module format"  when typing modprobe iwl3945  :(

---

