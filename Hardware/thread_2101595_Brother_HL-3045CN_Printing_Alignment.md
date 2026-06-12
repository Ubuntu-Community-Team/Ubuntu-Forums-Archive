---
title: "Brother HL-3045CN Printing Alignment"
date: 2013-01-05
forum: Hardware
---

### Post by XsisPwrs on 2013-01-05
I have a Brother HL-3045CN printer which is installed on my machine (Ubuntu 12.10) over the network. I can print but all the pages are off in the margin (too much to in the left and bottom) and maybe out of scale (can't tell). I got the driver from Brother's site and have tried reinstalling. I tried to check the 'Scale to Fit' option and have also toyed with /etc/cups/ppd/HL3045CN.ppd file ([https://bugs.launchpad.net/ubuntu/+source/brother-cups-wrapper-laser1/+bug/242203](https://bugs.launchpad.net/ubuntu/+source/brother-cups-wrapper-laser1/+bug/242203)). There is another printer in my network which is able to print perfectly (HP 6500 e710n-z) so I'm really stuck right now :(. I'm new to Ubuntu and linux as a whole and I really need help to get this printer working correctly. Thank you.

---

### Post by XsisPwrs on 2013-01-05
So I [kinda] fixed it. I played around with the imageable area setting in the ppd and restarted cups with scale page to fit. Now all the printed stuff is viewable. The margins are a little bit too big and the bottom one is slightly larger than the rest, but that's not a big problem. I only problem though, is that the page is out of scale when printed (a little too small). Well at least I can print now :P.

---

