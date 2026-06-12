---
title: "Install sees RAID when none exists"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by mooreted on 2009-11-08
Trying to install 9.10. It sees my onboard RAID controller which is disabled in BIOS. I have tried removing all drives but one by physically unplugging them. When I do that Ubuntu doesn't see any drives at all, it insists on having my fake RAID conroller enabled. I don't want to use fake RAID.

---

### Post by mooreted on 2009-11-09
Oh well, I'm running fake raid. Didn't have a choice. I'm going to file a bug report.

---

### Post by Ginsu543 on 2009-11-10
I had the same problem as you did but I got it to work by doing the following:
1) Unplugged all drives except the one I was installing to
2) Booted in live session with Karmic live CD (without installing)
3) Opened Terminal and ran sudo apt-get remove dmraid
4) Ran the installer by double-clicking its icon on the desktop

This allowed the installer to see my SATA drive by itself and not as a member of a non-existent RAID array. Once I installed the OS onto this drive, I shut down, plugged in my other drives, and rebooted. Now that everything is finally working right, Karmic is a very nice OS. One thing to note: if you install Gparted, make sure to sudo apt-get remove dmraid again because dmraid gets reinstalled as part of the Gparted package. There may be something broken with dmraid that may be causing all these problems.

---

### Post by mooreted on 2009-11-10
Thank you. Don't know why I didn't think of that.

For now I have RAID running. I keep constant backups, so I guess I can take this opportunity to see how reliable my onboard RAID controller is.

If no one has filed a bug report, I'm going to do so. We should have a choice.

---

