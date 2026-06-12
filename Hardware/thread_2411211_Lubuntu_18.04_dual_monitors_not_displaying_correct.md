---
title: "Lubuntu 18.04 dual monitors not displaying correctly"
date: 2019-01-27
forum: Hardware
---

### Post by Clueless Wonder on 2019-01-27
I installed Lubuntu-core (via 386 mini.iso)  on a USB flash drive and it works great when I have only one monitor plugged in.  When I plug  in a second monitor on the same card and set the displays to be extended (or joined) rather than mirrored, the screens become unreadable. Mirrored works  fine.  I tried adjusting the resolution and refresh rate for both, but  couldn't find a combination that worked.  Here is an image of one of the monitors.  It is the same on both.
[ATTACH=CONFIG]282320[/ATTACH]

$ lspci -nn | grep -E 'VGA|Display' shows
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, INC. [AMD/ATI] RV370 [Radeon X300] [1002:5b60]
01:00.1 Display controller [0380]: Advanced Micro Devices, INC. [AMD/ATI] RV370 [Radeon X300 SE] [1002:5b70] 

I have used this card before with Lubuntu with no problems, but that  was when it was installed on a hard drive, not USB flash drive.
  Does anyone have any suggestions or advice?  Let me know if you need more info.

---

