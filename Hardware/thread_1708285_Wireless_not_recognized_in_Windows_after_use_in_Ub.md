---
title: "Wireless not recognized in Windows after use in Ubuntu"
date: 2011-03-16
forum: Hardware
---

### Post by mnkpx7 on 2011-03-16
I am able to get online with Ubuntu. It automatically recognizes my wireless AP and connects. However, when I restart and load Windows, it will not find any wireless networks.

I'll have to test some more to be sure, but it seems that if I do a full shut down under Windows and then start it again, that clears the problem.

Anyone have ideas as to what's happening?

---

### Post by mnkpx7 on 2011-03-20
bump

---

### Post by mnkpx7 on 2011-03-21
Anyone?

---

### Post by rbishop on 2011-03-21
Problem = Windows!

I have more problems with Windows and wireless networking than I ever had with Ubuntu.

---

### Post by mnkpx7 on 2011-03-21
Point taken. I discovered it while trying to set up ubuntu because it happened in ubuntu as well. But I haven't been able to recreate that in ubuntu in a while.

---

### Post by coffeecat on 2011-03-21
> **mnkpx7 said:**
> I'll have to test some more to be sure, but it seems that if I do a full shut down under Windows and then start it again, that clears the problem.

I've come across something like this mentioned before. The explanation was that firmware is loaded into the wireless device by the operating system, but is left in an inconsistent state if you do a warm reboot from one OS to another. Why that should be different from doing a warm reboot in the same OS escapes me.

The answer seems to be if going from one OS to another, shut down completely, and then start up again.

---

