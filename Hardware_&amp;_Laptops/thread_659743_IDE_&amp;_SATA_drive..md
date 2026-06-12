---
title: "IDE &amp; SATA drive."
date: 2008-01-06
forum: Hardware &amp; Laptops
---

### Post by nyroshan on 2008-01-06
Hi. I'm relatively new to ubuntu, but this question isn't strictly ubuntu related. I have a Dell 8300 which had a SATA drive that has a large number of disk errors on. There were so many errors that windows would always do a disk check, and I couldn't even install ubuntu on the drive. So I bought an IDE drive and installed it as Master and put xp and ubuntu on it. I was then trying to copy the files over from the SATA to the IDE drive but, whenever I plug in the sata drive as well, it always boots straight off of that with the messed up windows installation that barely works. I checked through my bios (I was told that dell uses a custom bios) and couldnt find an option for which drive to boot off of other than setting them on and off. I'm hoping that someone out there can tell me how I could set the system to boot off of the IDE drive with ubuntu and xp but still use the SATA drive to retrieve my data off of. Thank you for taking your time to read this, and if you can please attempt to help me. Thank you.

-Roshan

---

### Post by rufius on 2008-01-06
Your issue is probably as follows:

Hard drives have jumpers, typically three (master, slave, check). I'd bet cookies to cakes that your SATA drive has its jumper set to "master" and your IDE drive has its jumpers set to "check".

What this means is, when you have the IDE drive plugged in with no other drives, it is automatically picked up as the master but when the SATA drive is plugged in, it is the master, thus making the IDE drive slave since it doesn't have the 'master' jumper set.

What you need to do is take your hard drives out and set the IDE to master, and the SATA to "check" or "slave". Doing this should solve your problems.

Here's some wikipedia information about it: [http://en.wikipedia.org/wiki/Integrated_Drive_Electronics#Cable_select](http://en.wikipedia.org/wiki/Integrated_Drive_Electronics#Cable_select)

Hope that helps :)

---

