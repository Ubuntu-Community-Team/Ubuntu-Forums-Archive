---
title: "Display turns off while boot"
date: 2013-07-17
forum: Hardware
---

### Post by geckon on 2013-07-17
Hi I have this problem with my laptop MSI ex630.

Yesterday I have disasembled it because it was overheating. I cleaned it up and applied thermal grease (Revoltec RZ032) on CPU and GPU (NVIDIA 9400 M). Then I played ~2 hours PC games (on Windows) and then rebooted to my Xubuntu 12.10 and browsed the web etc. Then I suspended to memory (as I always do) and went to bed. In the morning I wanted to resume my laptop but it waked up with the display turned off. I shutdown the laptop the hard way and tried to boot it again. 

Always I see grub, then I see "Xubuntu 12.10" and about the time when the log screen should emerge, the display turns off. It seems that booting stops at this point (according to inactive HDD LED even if I try to log in "blindly"). When I try to boot to Windows something similar happens. Normal boot turns display off and safe-mode boot shows a window in a bad resolution with something like ""Trying to identify and solve the problem." After it ends, reboot is required but obviously the problem is not solved.

I have a suspicion that GPU could be "broken" somehow. Can I somehow verify this? Do you have any other ideas? I am able to boot into safe-mode and use the root console. Where to look? Is there any console utility to diagnose problems on GPU?

Thanks a lot!

---

### Post by BreezyBrooke on 2013-07-17
Did you put it back together correctly? Unlike desktops, Laptops are very finicky. A missing cable, or one you forgot to plug in, misseated card, missplaced heatsink, a screw to tight or loose causing uneven contact on the chipset/CPU/GPU/casing causing overheating and damage, didn't work with an electrostatic band, ect..

---

### Post by geckon on 2013-07-17
Yes, I´m quite sure I have. I even disassembled it again and checked it. Also it worked few hours after the first disassembly.

---

