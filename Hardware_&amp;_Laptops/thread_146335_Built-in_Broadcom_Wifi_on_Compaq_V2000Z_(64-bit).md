---
title: "Built-in Broadcom Wifi on Compaq V2000Z (64-bit)"
date: 2006-03-18
forum: Hardware &amp; Laptops
---

### Post by Bondolon on 2006-03-18
Contrary to a plethora of posts that seemed to scream "I can't get this damned thing to work", I did.  However, that was in 32-bit.  As a bit of fun, I decided to reformat this weekend into 64-bit (Don't ask why I felt I had to completely reformat).  Anyway, as it boils down, I've tried everything short of reinstalling to get this WiFi to work, but can't.  As it was before, the thing would light up while the loading modules message was doing its thing.  If, by some damnable miracle, I managed to press the WiFi button, it wouldn't come back on, even if I rebooted.  I would have to reinstall the .inf in ndiswrapper.  However, this would solve the problem.  Now, however, I've still failed to get the WiFi to work at all.  ndis happily acknowledges that the hardware exists, but I understand that it's not actually "on", in the sense that the WiFi is "on" when the light is lit up.  I actually compiled the ndiswrapper-utils and -modules from source, so I know that they're working with my install.  Has anyone else had a similar problem that resolved itself in such a way that is similar to my 32-bit install's performance?

---

### Post by Steve1961 on 2006-03-18
[QUOTE=Bondolon]Contrary to a plethora of posts that seemed to scream "I can't get this damned thing to work", I did.  However, that was in 32-bit.  As a bit of fun, I decided to reformat this weekend into 64-bit (Don't ask why I felt I had to completely reformat).  Anyway, as it boils down, I've tried everything short of reinstalling to get this WiFi to work, but can't.  As it was before, the thing would light up while the loading modules message was doing its thing.  If, by some damnable miracle, I managed to press the WiFi button, it wouldn't come back on, even if I rebooted.  I would have to reinstall the .inf in ndiswrapper.  However, this would solve the problem.  Now, however, I've still failed to get the WiFi to work at all.  ndis happily acknowledges that the hardware exists, but I understand that it's not actually "on", in the sense that the WiFi is "on" when the light is lit up.  I actually compiled the ndiswrapper-utils and -modules from source, so I know that they're working with my install.  Has anyone else had a similar problem that resolved itself in such a way that is similar to my 32-bit install's performance?[/QUOTE]


Are you using the 64bit broadcom driver?  If not the 32 bit won't work on a 64 bit system, but there's a generic driver available [here.]("http://www.linuxant.com/driverloader/drivers.php")

---

