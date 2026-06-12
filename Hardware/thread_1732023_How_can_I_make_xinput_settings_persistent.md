---
title: "How can I make xinput settings persistent?"
date: 2011-04-17
forum: Hardware
---

### Post by jimmy the saint on 2011-04-17
This is very frustrating.

The mousepad on my laptop is kind of a POS.  In order to get multitouch to work, and to make the mousepad not freak out when my finger gets within 100 yards of it, I need to run a script setting specific xinput-prop values.

The problem is that any time I either plug in an external mouse or suspend the laptop or the screen goes blank, the values get reset and I need to run the script again manually.  This is a pain in... well you know where.

Short of running a cron job every minute, is there a way to make these settings persistent?  This was never an issue for me until 10.10.

Thanks

---

### Post by jimmy the saint on 2011-04-22
bumpity bump bump

---

### Post by mariogiov on 2012-03-27
Did you ever solve this? I'm facing a similar problem with a touchscreen that starts with the x-y coordinates all mixed up. I can use udev to run a script when it's plugged in, but the script runs as root so it doesn't affect my X session. I too would rather avoid a constantly-polling script. 

Maybe I just need to read more about configuring X. Another learning experience.

---

