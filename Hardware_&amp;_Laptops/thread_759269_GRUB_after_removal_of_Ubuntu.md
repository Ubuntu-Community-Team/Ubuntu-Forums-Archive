---
title: "GRUB after removal of Ubuntu"
date: 2008-04-18
forum: Hardware &amp; Laptops
---

### Post by Living2007 on 2008-04-18
I wanted to clean out my system from stuff I never used. And I the prosses, I remove Ubuntu purposely.

Now when ever I boot from my boot partition, it says
```
GRUB 2.2
Error 22
```

That's because I remove the Ubuntu Partition. Now XP won't load and i'm running on the Live CD. Which file do I remove so I can get back into XP w/o installing Ubuntu again.

---

### Post by overdrank on 2008-04-18
> **Living2007 said:**
> I wanted to clean out my system from stuff I never used. And I the prosses, I remove Ubuntu purposely.

Now when ever I boot from my boot partition, it says
```
GRUB 2.2
Error 22
```

That's because I remove the Ubuntu Partition. Now XP won't load and i'm running on the Live CD. Which file do I remove so I can get back into XP w/o installing Ubuntu again.

HI and this may help
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by VeN0mizer on 2008-04-19
For a simpler solution and much less reading, this happened to me recently on a computer I wanted to use the new install method on rather than multiple partitions, I deleted the linux partions only to get this message. I knew I needed to repair the boot record for windows....here's how! Find yourself a windows xp CD, any will do, stick it in, boot from it, select R when prompted to use recovery console, enter Admin password, when at the console, type "fixmbr" (without quotes) and you will get a nasty warning message that the world will end, etc, and it will since you are going back to windows, press yes or whatever, and in a split second your back in business, reboot, and viola, back to winblowz :)

---

### Post by Living2007 on 2008-04-20
WOW! I'll keep your tip, (only if I knew the Admin password), but I re-installed ubuntu on a 2GB  drive this time.

Thx

---

