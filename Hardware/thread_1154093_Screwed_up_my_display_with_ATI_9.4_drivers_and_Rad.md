---
title: "Screwed up my display with ATI 9.4 drivers and Radeon X1300"
date: 2009-05-09
forum: Hardware
---

### Post by linuxus95 on 2009-05-09
Hi and thanks for any help you guys can give. I am running Jaunty and I was currently messing with my display settings. I have an ATI Radeon Mobility X1300 Graphics Card. As the older versions (9.2 and 9.3) won't work with Jaunty, I installed the 9.4 drivers. Unfortunately, it was too late when I figured out that Radeon X1300 is not supported by the 9.4 drivers. Upon reboot, I just get a bunch of trash show up on the screen, and I cannot login.

Any help would be greatly appreciated.

---

### Post by Pépou on 2009-05-09
I had exactly the same problem yesterday.

Press escape when the computer starts and choice the rescue mode.
Then start the command lines and write :
*sudo apt-get remove fglrx**

Good luck.

---

### Post by linuxus95 on 2009-05-09
Thank you so much! I'm really happy I don't have to reinstall the whole OS and lose all my data!

---

### Post by NormanFLinux on 2009-08-03
The only workaround is open source drivers and editing the xorg.conf file. I had to reinstall the entire OS twice before I figured out the proprietary drivers are pita on 9.04. ATI has discontinued support for three year old cards and we're stuck with having to fiddle around every time Ubuntu is upgraded. Other than that, I'm happy.

---

