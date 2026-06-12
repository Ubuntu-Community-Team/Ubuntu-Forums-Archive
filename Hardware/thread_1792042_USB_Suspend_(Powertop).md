---
title: "USB Suspend (Powertop)"
date: 2011-06-27
forum: Hardware
---

### Post by zz0 on 2011-06-27
So, the other day I was running powertop, and it asked me if I wanted to disable non-input USB devices or something like that. So, I pressed U. Now, whenever I unplug the AC on my laptop, all of my USB devices stop working. Could the two events be related, or is this behaviour because of something else?

---

### Post by tgalati4 on 2011-06-27
On AC, open a terminal in full screen:

dmesg | tail -f

Pull the plug then watch the messages scroll by.

Then plug in a few USB devices, one at a time and observe any additional messages.

Powertop settings are only active during the current, booted session.  They revert once you reboot, unless you make changes to rc.local or some other bootup script.

I believe powertop disables HAL's 2-second USB detection rule, which can wake the processor and thus use more power.  I believe it's the timer that is the culprit, not the 2-second interval, but I would have to research it some more.

Also check your BIOS settings.  There may be a setting "Allow USB devices to wake computer" under Power Management.  See if there are any other USB-related settings that you can set.

---

