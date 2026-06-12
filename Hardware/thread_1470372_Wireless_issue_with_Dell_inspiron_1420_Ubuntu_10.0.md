---
title: "Wireless issue with Dell inspiron 1420 Ubuntu 10.04"
date: 2010-05-02
forum: Hardware
---

### Post by Micromega on 2010-05-02
Just installed the newest version of Ubuntu (10.04). When I click on the network icon in the top panel it indicates that wireless is disabled. I have gone through the process of installing the broadcom firmware and drivers, and the device indicates that it is active. I have found a workaround that consists in turning off the radio and rebooting. Once I have logged in I turn the radio back on, and then I can use wireless with no issues. I would like to not have to use this workaround. Just wondering if anyone has any suggestions. Many thanks.

---

### Post by Micromega on 2010-05-05
Seems to have been an issue with the wubi installer. I re-partitioned my drive and ran a full installation of Ubuntu 10.04. Wireless works fine now.

---

### Post by PGScooter on 2010-06-04
after you did the full installation of Ubuntu 10.04, did you have to do anything in order to be able to use your wireless? If so, can you give instructions? Thanks

---

### Post by Jonsan on 2010-06-04
If I were you, I'd try a direct connection to the router and see if your  connection stalls again. You could also consider changing channels or  getting another modem. What kind of modem do you have? Some people have  had problems with Motorola modems. Maybe you would like to try to reset  the router to factory defaults and  have it reconfigured.

---

### Post by Tburger on 2010-06-05
I installed Ubuntu 10.04 using Wubi and had major issues with getting wireless to work.  In the end I went with the older b43 install (instead of the STA), and then blacklisted dell-laptop.  After that, it worked!  I'm on a Dell Insprion 15?? using a Dell Wireless 1397 (same as BCM4312).  The fix I found for testing the removal of dell-laptop and then blacklisting it is [HERE.]("http://ubuntuforums.org/showthread.php?t=1414946&highlight=dell-laptop")
(You have to scroll down a bit to find the instructions)

---

