---
title: "xserver-xorg-core update breaks suspend"
date: 2008-01-19
forum: Hardware &amp; Laptops
---

### Post by rockin_goliath on 2008-01-19
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/184492](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/184492) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hey everyone! I just installed the recent update to xserver-xorg-core (Version 2:1.3.0.0.dfsg-12ubuntu8.3) and the suspend on my laptop stopped working. I would open the lid, type my password, and my session would open, but after a few seconds the whole system would freeze up, I couldn't even use ctrl-alt-backspace! I solved the problem by forcing the previous version in Synaptic (select the package, then go to Package - Force Version and select the previous version in the list), however I am a little concerned about doing that as it was an "Important Security Update" fixing things such as memory corruption. Microsoft recently did a press release about how corrupted header information in Word and Excel files that corrupted system memory was a big security risk, but I don't know if those are related. There was another post about an update to version 8.2 and how it broke Java applications ([http://ubuntuforums.org/showthread.php?t=671020](http://ubuntuforums.org/showthread.php?t=671020)) but apparently update 8.3 fixed that, I also don't know if they are related. 
I filed a bug at Launchpad.

Forgot to mention that I am using a Dell Inspiron 600m, Intel Pentium M 1.7 ghz, ATI Mobility Radeon graphics.

---

