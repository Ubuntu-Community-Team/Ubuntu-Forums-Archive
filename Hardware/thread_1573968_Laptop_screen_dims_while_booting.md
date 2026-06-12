---
title: "Laptop screen dims while booting"
date: 2010-09-13
forum: Hardware
---

### Post by mia777 on 2010-09-13
Greetings.

I have a brand new laptop and whenever the system boots up, the text in the console begins to sequentially dim. When gdm loads up, it too is dim and I cannot make it any brighter.

Any tips on debugging this issue?

UPDATE - I can now reproduce this issue.

I am trying to use an nVidia driver so I'm playing around with my X.org configuration.

When I boot after making changes, X starts in "low-graphics mode"  because "(EE) No devices detected." (no screens found). The screen is  very dim.

Oddly, if I RESTART while debugging X.org (after pressing okay in the  "Ubuntu is running in low-graphics mode"), the Phoenix BIOS screen is  dim, as is the Grub2 boot menu, and everything thereafter.

If I exit it to the console and HALT, the Phoenix BIOS is screen is once  again "bright" (seems like the backlight is on), as is the Grub2 boot  menu, and X (GDM, etc.).

[B]It seems like some "dim" setting is persisting on reboot after entering low-graphics mode.

Is this supposed to happen? Can anyone comment on this.
[/B]

Thanks,
Ryan

---

### Post by mia777 on 2010-09-13
An update: after playing with the display settings and constantly rebooting after I changed them, I finally shut the laptop off, unplugged it, and then replugged it and booted. Now the Phoenix BIOS screen and the Grub2 boot selection window are all brighter. 

What might be causing this issue?

Thanks,
Ryan

---

### Post by bosna110 on 2010-09-13
ive had that problem and still having it. when i press the power button to my laptop to power it, it'll display my gateway logo and then dim everything after that.

---

### Post by mia777 on 2010-09-13
UPDATE - I can now reproduce this issue.

I am trying to use an nVidia driver so I'm playing around with my X.org configuration.

When I boot after making changes, X starts in "low-graphics mode" because "(EE) No devices detected." (no screens found). The screen is very dim.

Oddly, if I RESTART while debugging X.org (after pressing okay in the "Ubuntu is running in low-graphics mode"), the Phoenix BIOS screen is dim, as is the Grub2 boot menu, and everything thereafter.

If I exit it to the console and HALT, the Phoenix BIOS is screen is once again "bright" (seems like the backlight is on), as is the Grub2 boot menu, and X (GDM, etc.).

[B]It seems like some "dim" setting is persisting on reboot after entering low-graphics mode.

Is this supposed to happen? Can anyone comment on this.
[/B]
Thanks,
Ryan

---

### Post by bosna110 on 2010-09-13
is there any way i can record how my boot loads so i can show you? the only way for me to actually fully boot without a dim problem is to hook up my laptop to a secondary monitor and when it is booted i can use laptop... this is like really oddly strange. let me know if anyone can help. Thanks

---

