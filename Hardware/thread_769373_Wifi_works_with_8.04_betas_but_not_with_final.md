---
title: "Wifi works with 8.04 betas but not with final"
date: 2008-04-26
forum: Hardware
---

### Post by umbra_rex on 2008-04-26
Hi everyone. I'm using an HP TX1417cl with a Broadcom 4321AG 802.11a/b/g/draft-n wifi adapter. When using ubuntu or xubuntu 8.04 betas the restricted driver manager could see my wifi card and everything was working flawlessly. I want to do a clean install of 8.04 final, but when I install it the restricted drivers manager cannot see my wifi card. When I run iwconfig in a terminal it dose not find any wireless network adapters. 

I'm wondering if there is away to get ubuntu 8.04 final to see my wifi card, or if I should try reinstalling the beta release and running the partial upgrade? 

Thanks for your help,

umbra_rex

---

### Post by gururise on 2008-04-26
Some broadcom driver support was pulled from Ubuntu at the last minute due to some problems.  This is probably what happened to you.  You will have to wait until Kernel 2.6.25 is released for ubuntu to fix this problem, or possibly compile a kernel yourself (thats what I did).

---

