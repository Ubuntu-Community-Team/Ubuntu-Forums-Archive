---
title: "Some inconsistencies with suspend"
date: 2013-09-16
forum: Hardware
---

### Post by Quackers on 2013-09-16
I have a MacBook Pro retina and am running 13-04 amd64+mac with the Nvidia driver.
I'm also running gnome-shell and, therefore gdm rather than lightdm.
It is set to suspend when the lid is closed in the settings.

When I click on the menu and choose suspend absolutely nothing happens - the system stays live.

When I close the laptop lid the laptop suspends ok. However on wakeup the system is running but the screen is a sort of mid-grey 
colour - no desktop visible or pointer. 
I know everything is working because if I do ctrl+alt+t and do a sudo reboot then enter my password (even though I can't see anything) the system will reboot.

Now here's the kicker - if I run pm-suspend in the terminal the system goes into suspend. Closing the laptop lid leaves it in suspend.
Opening the laptop lid wakes the system up again and the system is then working fully.

Where should I look for possible troubleshooting purposes?
Does anything spring to mind regarding possible causes?

Thanks.

Bug reported
[https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/1226369]("https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/1226369")

---

