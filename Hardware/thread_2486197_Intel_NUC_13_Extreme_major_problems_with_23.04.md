---
title: "Intel NUC 13 Extreme major problems with 23.04"
date: 2023-04-22
forum: Hardware
---

### Post by yottabit2 on 2023-04-22
I bought an Intel NUC 13 Extreme for photo and video editing in Linux after many years using a NUC 5 for the same. I've been very disappointed so far.

I've tried Ubuntu 23.04, Debian Bookworm, and the latest Fedora... None of them support the built-in wireless. Come to discover, it's just because the wireless card's ID numbers are not listed on the iwl driver from Intel, and if you patch the driver manually with the IDs, it works fine!

Next, the built-in igc 2.5 Gbps Intel Ethernet flaps occasionally when under heavy load, which really makes transferring these large media files a problem, and working live from a Samba or NFS share could even be dangerous.

Then there's the monitor timeout... If I leave the computer and the monitor is turned off for power saving, it will not turn on again when I come back to the computer unless I unplug and plug in the HDMI cable! This happens even with the regular Sleep power saving disabled. The monitor will wake up, but never show a picture, and then go to sleep mode again.

And finally there's a weird display bug with ART (Rawtherapee fork). If I'm in the editor and flipping backyard and forward through pictures, each time the picture changes the application resizes by removing a line or two from the bottom. After using it for a while editing photos, the "full screen" window now has a large gap at the bottom and I have to restore the window size and then maximize it again.

All in all, this has been a pretty disappointing experience, and most of it is Intel's fault slacking off as usual. 

If anyone happens too have any inside knowledge that any of these problems are going to be addressed soon, please let me know! I'm posting this more of a warning than a help request, since I don't think much is likely to change until Intel fixes their bugs. But maybe the monitor sleep issue could maybe be an Ubuntu problem. Maybe.

---

