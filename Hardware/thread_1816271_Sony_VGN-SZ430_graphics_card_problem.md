---
title: "Sony VGN-SZ430 graphics card problem"
date: 2011-08-01
forum: Hardware
---

### Post by outlaw979 on 2011-08-01
Hi all,
 First of all I have to say I'm very new in the Linux world and recently decided to install Ubuntu 11.04 on my Sony vgn-sz430n laptop alongside with its original Vista.
 On the first boot after installation I've got the message saying something like: "Graphics card couldn't detected therefore Ubuntu will run in Classic mode "
I downloaded the latest driver (275) from Nvidia site for GeForce Go 7400 (which is my laptop's graphics card) but it didn't solved the issue.
Is there anybody here that can help me? :(

Any feedback will be very appreciated!

---

### Post by gordintoronto on 2011-08-01
After downloading the driver, did you do anything with it?

Have you tried System/Administration/Additional Drivers?

According to the Sony web site, your computer has: NVIDIA® GeForce® Go 7400 and Intel® Graphics Media Accelerator 950

In other words, it has switchable graphics between low power and high performance. If you run Accessories/Terminal and enter the command:
lspci
it will display about 15 lines. One of them will contain the word "VGA," and that describes what graphics adapter is active. Is it actually the Nvidia, or is it the Intel?

I don't think Linux fully supports the switchable graphics yet, but I could be wrong.

---

### Post by outlaw979 on 2011-08-02
Yes you're right my laptop has a switchable graphics, I didn't think about that when I installed Ubuntu, and it was on Perfomance mode (Nvidia 7400 card).
Regarding Nvidia 275 driver - I installed it (with help from my work colegue) but this didn't solve the issue with unity.
When I switch graphics to Intel ubuntu boots up with Unity interface with no issues.

---

### Post by realzippy on 2011-08-02
[http://ubuntuforums.org/showthread.php?p=10304516#post10304516](http://ubuntuforums.org/showthread.php?p=10304516#post10304516)

---

