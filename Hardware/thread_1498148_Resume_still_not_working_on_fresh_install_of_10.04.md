---
title: "Resume still not working on fresh install of 10.04"
date: 2010-05-31
forum: Hardware
---

### Post by alexazul on 2010-05-31
I cannot resume my Samsung NC10 (freshly installed Ubuntu 10.04, updated BIOS and kernel) while on battery power. When I press the power button to resume, I'm greeted with a frozen (but normal-looking) screen. 

The only setup that works for me is when I suspend from the system menu with my AC cord plugged in. If I do anything differently (no AC cord, pressing the "Sleep key" [Fn + F1] and by closing the lid) then I'm unable to resume. When I awaken the computer (using the power button) I get only a frozen screen and cannot use any controls. I'm forced to shutdown by holding down the power key.

Does anyone have any ideas where I should go from here? I'm getting the idea that everyone else has worked out a solution to this problem, except me. I've spent the last week trying to fix this. I've searched through these forums, Launchpad, Google, and everywhere else I could think to look. I found one bug that I thought was related ([#340014]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/340014")) but apparently it is not, so I've opened a new bug on Launchpad ([#586996]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/586996")). For what it's worth, I've tried commenting out pm-powersave and booting with nohdparm, neither of which made a difference.

---

### Post by alexazul on 2010-06-01
Bump. Can anyone help out with this? I know I'm being the annoying newcomer here, but I really, really want to make Ubuntu work. I just have no idea where to go from here.

---

