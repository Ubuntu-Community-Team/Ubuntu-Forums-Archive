---
title: "Wireless wont work and no system settings"
date: 2011-01-26
forum: Hardware
---

### Post by MasonShadows on 2011-01-26
Well I am using a HP Pavilion dv6-1242tx and the wireless wont work.  I have read lots of howtos and solutions and none work.  nd to top that off my system settings is missing it isn't in the menu or anything! I need help bad.  And thank you to anyone who helps!

---

### Post by gordintoronto on 2011-01-26
What is the wireless device? If it's USB, open Accessories/Terminal and run this command:
lsusb
otherwise, this one:
lspci | grep 802

Also tell us what version of Ubuntu you are using?

I don't know what you mean by "system settings". Perhaps you mean System/Preferences?

---

