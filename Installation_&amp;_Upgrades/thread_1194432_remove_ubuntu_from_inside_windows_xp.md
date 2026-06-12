---
title: "remove ubuntu from inside windows xp"
date: 2009-06-22
forum: Installation &amp; Upgrades
---

### Post by mayogirl on 2009-06-22
Hi
I am new to linux.  I installed ubuntu inside windows and really like it.  Now I want to set up a dual boot system.  I uninstalled ubuntu from add/remove programs in windows control panel.
When I restart I still get option for ubuntu but goes nowhere if I choose it.


This is my boot.ini

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"

Question is - can I just delete last line and then do a dual boot from ubuntu cd.  Or should I just do clean install of windows and continue from there ?

---

### Post by wpshooter on 2009-06-22
I really don't know what the affect of deleting the line would be, so I think instead I would just comment it out for the moment and then reboot and see what the affect is.

I think I would also make a backup of the file just as it is now before making any changes to it, just in case.

---

### Post by presence1960 on 2009-06-22
C:\wubildr.mbr = "Ubuntu"

remove that line _ONLY!_, that is why you are getting the option to choose Ubuntu even though you removed Ubuntu. **_Do not edit the other info or you may not be able to boot!_**

---

### Post by mayogirl on 2009-06-23
Thanks for help.
I removed that line and all seems fine.

---

