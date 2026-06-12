---
title: "kernel detecting wacom tablet intermittantly"
date: 2015-10-26
forum: Hardware
---

### Post by eric94 on 2015-10-26
I have a Fujitsu Stylistic ST5112 tablet that I started on Xubuntu 12 and have upgraded as the software advanced.  Resent updates for xubuntu 14LTS caused the Wacom pen tablet to stop working.  So I updated to 15.10 hoping things would be fixed.  Then things got weird.  It worked fine after the system upgrade.  I was happy to be back in business.  Then I shut it down and the next time I booted it up the tablet it didn't work.   I plugged in a keyboard and mouse and popped into terminal.  Tried (dmesg | grep -i wacom)  No reply.  Tried (xsetwacom --list devices)  Nothing.I thought maybe the system was getting dodgey from the after effects of several upgrades.  So I backed up my data and did a clean install from USB.  Again it worked first time after install and quit after that.  Occasionally it will work when I boot it up.  Maybe 1 in six tries.I don't think it's a hardware issue as the wacom pen layer works just fine in the bios every time during the boot.  It seems like the kernel isn't always seeing the device.  When it does detect it everything shows as normal. The wacom input device appears in the settings menu.  When you check it in the terminal it looks fine as wellAny advice would be appreciated.  Thanks

---

