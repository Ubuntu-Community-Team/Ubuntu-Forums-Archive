---
title: "Important!!!"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by CD27 on 2009-11-01
The other day I upgraded from Ubuntu 9.04 to Ubuntu 9.10. In the middle of the upgrade (via command line with the code: "do-release-upgrade") it errored out. I don't know why, but it kept telling me something about some kind of bug. I showed it to someone, they said the upgrade still went through and should be fine, just reboot. So I rebooted. Upon bootup I recieved an error. I can't remember precicely what it said, except that it stated something with UUID's and could not mount the hard drive. I booted to my 9.04 live cd, figured i'd just reinstall 9.04 and then do an upgrade from a fresh system. The install kept hanging upon partitioning menu. I couldn't understand why, but for some reason, it simply couldn't read the hard drive. I was able to burn the new 9.10 version of ubuntu and tried it that way, nothing, same problem. I tried gparted, same thing. It simply wouldn't read the hard drive and upon bootup it couldn't boot the hard drive. We tried to manually correct grub, but it wouldn't take.

Finally as a last resort before literally using a wipe disc to wipe my hard drive entirely, i put in a windows xp isntall cd. It was able to read the partition tables and eventually was able to format them. I then quickly existed the install once it completed the format, and was able to successfully install 9.10 on my computer and everything is fully functional.

If i had not had that windows cd I would have assumed my hard drive was shot and either bought a new one or attempted to contact the company for a replacement.

I know there are multiple ways the upgrade could have failed, etc. etc. and that there might be something wrong with my install cd or maybe something was up, i don't know. Fact is gparted didn't read the partitions and neither did the install discs. It was by mere luck that windows was able to.

Is there a fix for this or something? What if someone's upgrade just stops in the middle of them and they don't know they can use windows to fix it? i mean these hard drives aren't cheap if you go out and buy good ones. I've only heard of a couple of people who have run into this problem, but I think it needs to be addressed just in case it happens in the future.

---

