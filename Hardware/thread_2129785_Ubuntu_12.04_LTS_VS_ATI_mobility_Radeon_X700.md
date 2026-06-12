---
title: "Ubuntu 12.04 LTS VS ATI mobility Radeon X700"
date: 2013-03-27
forum: Hardware
---

### Post by Selz on 2013-03-27
Hello everybody ! 

I just installed ubuntu 12.04 LTS on my laptop (Acer Aspire 1690) and i'm having trouble with my ATI mobility Radeon X700. I saw a lot of topic about that problem, but never found a definitive answer (good or bad).
The graphic card is noticed as "unknown". 

Could anyone please help with this ? (i'm kind of a newbie on linux)

I just sent a mail to the AMD technical support and i'm waiting for the answer (i'll let you know about it).


Thank you very much for your help !

---

### Post by Mark Phelps on 2013-03-27
If you're using System Info and it's telling you "unknown" -- that is a known bug with System Info.

You can find out what video chipset that Ubuntu is seeing by running the command "lspci" (without the quotes) and looking for the line containing "VGA".  It will probably say something like: RV410 Radeon X700.

If you're seeing a desktop, then the Radeon drivers are already installed -- and there's nothing more you can do as AMD dropped restricted driver support for this video chip years ago.

---

### Post by Selz on 2013-03-27
Thx you for answering me so fast !

So i did what you asked, and indeed, i can see the reference of my CGU. So... i guess it's good and thx you =)

But i got another little issue... Indeed, my laptop seems waaaay more slower than when i was on XP pro.. and i was thinking it'll be the opposite ! (Ubuntu is well known to be the faster OS... no ?)

Do you see something i could do wrong ? (again, i'm a newbie, for know i just installed ubuntu and didnt do anything else. Maybe there's some things i should do ?)

Hm, sorry for that question, bottle in the see =)

Thx you !

---

