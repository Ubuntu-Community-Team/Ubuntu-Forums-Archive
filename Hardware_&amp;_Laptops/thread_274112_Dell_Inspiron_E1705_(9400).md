---
title: "Dell Inspiron E1705 (9400)"
date: 2006-10-09
forum: Hardware &amp; Laptops
---

### Post by raexis on 2006-10-09
I have a Dell nspiron E1705 with a Dell 1390 integrated wireless adapter. I've installed Ubuntu 6.06 Dapper with the linux-686-smp kernel. Everything runs beautifully except for the OS doesn't even recognize the wireless card under System->Aministration->Networking. It only shows up as an "unknown device" when I run an lspci.

I've tried installing ndiswrapper through Automatix, then I loaded up the windows-based inf file which it recognized and statd that it successfully installed. However, when, I go back to networking or run an iwconfig, nothing shows up. I've also tried uninstalling ndiswrapper and compiling it from source code only to ahcieve the same effect...perfect installation right until the point that wlan0 never shows up.

Suggestions? I'd rate myself as a moderately experienced Ubuntu user so don't be afraid to throw out fairly technical help.

---

### Post by Kateikyoushi on 2006-10-09
[This thread might help]("http://ubuntuforums.org/showthread.php?t=193350").

---

