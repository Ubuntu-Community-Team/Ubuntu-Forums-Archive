---
title: "Reason for blinking caps lock light?"
date: 2011-11-17
forum: Hardware
---

### Post by Los Frijoles on 2011-11-17
So, I just booted my computer (Acer Aspire One (AOA 150) with Ubuntu 9.04 or something...I'm in the process of getting the new iso for a new install) after two years of non-use and found that it had a new development: Sometimes the screen goes black with just the cursor, the caps lock light blinks, and it is completely frozen. I read that this is usually a sign of a kernel panic, but I am wondering which log file to read to find out why.

Also, if anyone happens to have had this problem with an Acer Aspire One and has a solution that would be appreciated.

Thanks.

---

### Post by gordintoronto on 2011-11-17
A new version of Ubuntu will probably solve this. Google turned up an example where it was the wireless driver in 8.10, and for most people using "backports" solved it.

---

### Post by lswb on 2011-11-17
If the kernel was able to log any messages before the freeze you should find them in /var/log/syslog or /var/log/messages

---

### Post by Los Frijoles on 2011-11-18
I took at look at those log files and I don't know if it did managed to record anything (they just had the normal stuff...except there was a lot in there about the wireless card...so maybe the wireless driver was messed up like that google example). I finally managed to use another computer to download the iso for the Ubuntu 11.10 (with my computer failing all the time it just wouldn't download completely) and installed it and since then there hasn't been an issue.

Thanks!

---

