---
title: "GPU lockup"
date: 2020-02-06
forum: Hardware
---

### Post by d2105284 on 2020-02-06
My 18.0.4 system is "crashing" periodically.  When it happens the monitors shut off (as if the system was suspended) and Ctrl + Alt + F1-7 do nothing.  Keyboard and mouse are unresponsive, though the Num Lock light stays illuminated.  Always have to pull the power plug and reboot.

Here's the output of [FONT=courier new]journalctl -b -1[/FONT][URL="https://paste.ubuntu.com/p/NjbrxzZMKh/"]
https://paste.ubuntu.com/p/NjbrxzZMKh/[/URL]

Video card is [apparently]("https://everymac.com/systems/apple/mac_pro/specs/mac-pro-quad-core-3.7-xeon-e5-gray-black-cylinder-late-2013-specs.html") a (pair?) of AMD FirePro D300.  This has been happening quite a bit and I can't find a specific trigger that causes it though it always seems to be within a few seconds of keyboard or mouse input

---

