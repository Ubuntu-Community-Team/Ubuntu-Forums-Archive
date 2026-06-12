---
title: "Getting a &quot;Mode Not Supported&quot; on monitor"
date: 2007-07-02
forum: Hardware &amp; Laptops
---

### Post by blackspyder on 2007-07-02
I have been running Ubuntu Studio and recently decided to switch back to regular Ubuntu as there was too much stuff that I wasnt using. Anyway everything worked fine with U.S. but on regular Ubuntu my monitor blacks out and gives me the message "Mode Not Supported" and the Frequencies of the Horizontal and Vertical wich are around 15Hz for both.

The screen resolution is 1280x1024
Video Card is ATi Radeon 9250 and I havent installed drivers for it since I didnt have to for U.S.

Any help is greatly appricated.

---

### Post by fongs on 2007-07-02
try going for lower resolution 
sudo dpkg-reconfigure xserver-xorg
then go through change nothing except when you come to resolution hit space bar to change resolution.

---

### Post by blackspyder on 2007-07-02
I think I figured out what it was. In the Administartion menu Display settings it was shown as being a CRT monitor when its an LCD. However I already installed F7 over Ubuntu (F7 was doing the same thing). I still have KUbuntu installed on my laptop so Ill still be around.

---

