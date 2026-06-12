---
title: "&quot;Thaw&quot; error with Hibernation in Jaunty"
date: 2009-06-15
forum: Hardware
---

### Post by Alvin Chiu on 2009-06-15
I have a ThinkPad T40 with Jaunty installed.  Every time I set the computer to hibernate it will always spit out this:

[FONT=Courier New][   75.286416] pm_op(): pci_pm_thaw+0x0/0x50 returns -16
[   75.286420] Device 0000:00:00.0 failed to thaw: error -16

[FONT=Verdana]Eventually it does go into hibernation, but I was wondering if anyone knows what's conflicting with hibernation and if there is some way to fix this.[/FONT][/FONT]  Thanks in advance.

---

### Post by MakisM1 on 2009-07-12
Same problem, but when it comes out of hibernation it does not work properly and have to re-boot.

Any suggestions?

I have a dual boot with WXP, each one on its own drive, with a swap partition. I had a similar setup (WXP, swap partition, root directory partition and home partition) in one drive in my (now deprted) laptop and worked fine.

Does it make any difference that the boot loader is on the other disk with the WXP?

I read the topic about doing away with the swap partition and using a swap file instead, but I am not sure whether this is the right way to go.

[http://ubuntuforums.org/showthread.php?t=1042946&page=2](http://ubuntuforums.org/showthread.php?t=1042946&page=2)

Best regards

MakisM1

---

### Post by Alvin Chiu on 2009-07-15
Sorry MakisM1, but I've only used linux for a few months, so I'm probably not the best person to ask.  You could try looking around in the forums.

I haven't used a swapfile before because my hibernation mode seems to work using a swap partition (if I ignore the "thaw" error messages).

Good Luck,
Alvin

---

