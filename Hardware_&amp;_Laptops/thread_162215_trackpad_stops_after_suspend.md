---
title: "trackpad stops after suspend"
date: 2006-04-18
forum: Hardware &amp; Laptops
---

### Post by yankees26 on 2006-04-18
I recently successfully compiled and booted a 2.6.16 kernel (2.6.16.7 with a ck patch and soon hopefully with bcm43xx support).  Also, I can successfully suspend the computer to my swap partition, but when I wake the computer up from a suspend the trackpad no longer works.  Any help/advice to fix this would be appreciated.

---

### Post by trent dillman on 2006-04-18
You could remove the driver and reload it when your computer wakes up. See /etc/hibernate/hibernate.conf. Just be sure to back it up before you go poking around....

Also, are you on Breezy? You should try reinstalling (NOT upgrading) with Dapper. My laptop now has proper suspend/hibernate with no patching or recompiling!

---

### Post by yankees26 on 2006-04-18
I'm download Dapper now.  I originally planned on waiting but then when the bcm43xx modules wouldn't load, I gave up.  So, I'm taking your advice and going with Dapper because of the suspend ability and bcm43xx.

UPDATE
I installed Dapper, but the trackpad was extremely slow and even after setting the speed and sensitivity to max their was no gain in speed.  Also, my bluetooth mouse doesn't work(same exact stuff that happened when I tried Flight CDs 4 and 5 of Kubuntu).  Also, I couldn't get internet even after installing the firmware and stuff.  I'm going to wait until the final release.  Since I'm on April Break, I've got time to experiment.

---

