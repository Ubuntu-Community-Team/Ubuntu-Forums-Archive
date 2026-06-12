---
title: "Acer Aspire 5100 Wireless connectivity not working"
date: 2009-08-28
forum: Hardware
---

### Post by supreme_piccolo on 2009-08-28
Hi to any and all who can help
I need some help, I'm not sure if anyone else has had my exact problem so I started a new thread, hoping for some help. We got an not so used Acer Aspire 5100 from a friend that had windows 7 ultimate edition on it. We used the windows for a little while to test things out. The wireless connected just fine, we then put in the Ubuntu 9.04 in and made it the new OS. We then tried to connect to our internet but it wouldn't look for connections it would say "no wireless networks found" when I click on the connection icon, even though my other windows laptop is using our wireless just fine. 
 I checked the hardware drivers and found that there were two wireless drivers listed, both not active Broadcom B43 wireless driver and Broadcom STA wireless driver. I activated the STA because the B43 wouldn't work saying "fwcutter is a tool which can extract firmware from various source files. It's written for BCM43xx driver files" and then going blank. Then it told me promptly to reboot to activate the STA driver but when I do it goes back to being inactive. 
I know very little about how to make things work on a comp and know next to nothing about ubuntu and how it works being relatively new to this, if anyone could help me out with getting the wireless to work with lengthy steps if I have to use the terminal, that would be great. I'm not sure why things aren't working since the change from windows to ubuntu.

thanks in advance

---

### Post by supreme_piccolo on 2009-08-29
Well we played around with the computer some more and managed to get the wireless working for now. We went into hardware drivers and activated the driver for the third time and rebooted, Third time I guess is a charm. We did try to add some things to get the ndiswapper which we  found on various pages as a fix but couldn't find one for 9.04. I hope this helps anyone else who is having problems.

---

### Post by Phreak5758 on 2009-08-29
I'm using 9.04 on an AAO zg5.  I ended up using ndiswrapper 1.9 and finally got mine to work.

---

