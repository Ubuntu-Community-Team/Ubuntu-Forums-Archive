---
title: "Screen Brightness stays dim? (Tried a few methods already)"
date: 2013-02-26
forum: Hardware
---

### Post by wep11 on 2013-02-26
Good afternoon,

I'm running a Eee PC 900 with xubuntu and am having trouble changing screen brightness. Basically the screen stays at a constant dim brightness. The original LCD screen was damaged so I purchased an LED screen to replace it. I'm assuming the physical installation is fine since the backlight is lit.

The system Fn keys interact with xubuntu perfectly and indicate to me that there is a problem interfacing with the hardware. Naturally, I sought out the internet to find a simple solution. I attempted the grub fix by changing the line {  GRUB_CMDLINE_LINUX="quiet splash" }. It did not change anything.

Next I found a terminal solution that would use the /sys/class/backlight files. When those were not working I decided to look into the system files and discovered that MAX_BRIGHTNESS=15 , and ACTUAL_BRIGHTNESS=15 which indicates to me that this dim setting is already at its brightest.

Any ideas?

Thanks

---

### Post by wep11 on 2013-02-26
Oh, and just to add, I never had xubuntu installed before I replaced the screen. I replaced the screen back when I was on xp (Same problem though), I just haven't addressed the problem until now.

---

