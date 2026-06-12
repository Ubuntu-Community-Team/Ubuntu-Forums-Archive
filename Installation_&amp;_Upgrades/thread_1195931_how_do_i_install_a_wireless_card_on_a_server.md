---
title: "how do i install a wireless card on a server?"
date: 2009-06-24
forum: Installation &amp; Upgrades
---

### Post by celliott on 2009-06-24
Hi,

I have a server and its been running great for over a year. Well i just bought my own place and it isn't wired. I would like to use my server until i can figure out how to wire up the house.

I have a spare wireless card that is detected by the system, but how to i add the wep key / credentials to it?

I do not use any desktop manger, simply terminal.

Thanks,

Chris Elliott

---

### Post by milton1 on 2009-06-24
I believe there is a 'key'flag in iwconfig. Try ```
man iwconfig 
``` for details. 

PS - WEP is very easy to crack these days. Suggest you switch to WPA2.

---

