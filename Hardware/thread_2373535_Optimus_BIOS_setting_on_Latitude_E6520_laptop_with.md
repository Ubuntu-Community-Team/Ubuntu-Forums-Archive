---
title: "Optimus BIOS setting on Latitude E6520 laptop with hybrid graphics broken in 17.10"
date: 2017-10-07
forum: Hardware
---

### Post by horizonbrave on 2017-10-07
Hi,
 I own a Latitude E6520 laptop with hybrid graphics (Intel HD 3000 + Nvidia NVS 4200 Quadro).
 I'm trying to install Ubuntu 17.10 and only use the open source provided drivers (Nouveau), and I'm confused regarding enabling Optimus  in the BIOS or not.
After installation when I try to open a virtual console I get a blank screen with a blinking cursor (now Optimus is enabled in the BIOS).
Please any advice?

 Cheers :)

---

### Post by RobGoss on 2017-10-07
Please see this thread it explains in detail how to correct this issue hope this helps [https://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](https://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

---

### Post by horizonbrave on 2017-10-08
> **RobGoss said:**
> Please see this thread it explains in detail how to correct this issue hope this helps [https://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](https://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

The Live ISO just boots fine with both BIOS settings, and in both UEFI and legacy mode.

If I disable Optimus in the BIOS after a while the whole system freezes  (the laptop should use only the discrete graphics this way).
If I enable it no freezes/crashes but I can't open a virtual console  (blank screen with blinking cursor only) nor rebooting the system (it  hangs again on a blank screen with a blinking cursor) [IMG]https://ubuntuforums.org/images/smilies/icon_sad.gif[/IMG]
Cheers

PS.
Actually, If I boot in UEFI mode I get the following error message on screen (on Fedora too, sorry for cross-linking) but everything seems to work fine afterwards:
[https://www.forums.fedoraforum.org/showthread.php?t=315712](https://www.forums.fedoraforum.org/showthread.php?t=315712)

---

### Post by horizonbrave on 2017-10-10
I actually filed a [bug report]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1722639")

---

### Post by horizonbrave on 2017-10-24
Same thing happening on a Dell E6530 Latitude laptop. Live image works ok (virtual console are accessible) but after installation I just get that ame blank page again :(

---

### Post by RobGoss on 2017-10-29
Yes I have a Dell  Dell Latitude 610 and have never been able to get Ubuntu installed on it, Might be a hardware thing not sure

---

