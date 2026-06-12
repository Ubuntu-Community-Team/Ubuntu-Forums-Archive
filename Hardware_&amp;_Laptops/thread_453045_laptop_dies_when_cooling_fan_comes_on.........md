---
title: "laptop dies when cooling fan comes on........"
date: 2007-05-23
forum: Hardware &amp; Laptops
---

### Post by tachum on 2007-05-23
I have a Compaq Presario 2500 (2568AP) which has given around 3-4 years of good service. I have an XP /ubuntu 7.04 dual boot set up. This series of laptops does not use the centrino processor, but is more the old style 'desktop' .

I recently ran Fedora 6 on it and experienced a number of shutdowns due to 'critical tempertaure being reached'. I took it to the local compaq dealer who cleaned it up a bit inside but said it was ok. XP was not affected. I know there is a bug for this in the linux kernel for the critical temp being reached. . 

I installed 7.04 a few weeks ago and it has run fine. I do all updates. Last week, the laptop started freezing when the cooling fan came on. Usually ran for 10 to 15 minutes. XP does the same: the screen goes blank , and most of the lights stay on ie a freeze. Again, about after 10 minutes. 

Could it be that this style of laptop runs hotter than the new style of laptop, and the kernel can't accept this?

Is this hardware or software?? Any thoughts????

Thanks!

---

### Post by cantormath on 2007-05-24
It sounds like your acpi is not configured and/or working correctly.  This is generally do to the brand of bios you have.  If it is made by a company that refuses to support linux use and there has not been a "work around" created to fix the problem, you are screwed and you need a new bios or you need to wait till the problem is fixed.  

If you have had the acpi work properly but it stoped working properly after an update, it was probably a kernel update.  I would go back to the kernel that works and be more careful when updating.  

hope that helps

---

### Post by tachum on 2007-05-24
Thanks for that. I might just go back to Dapper, which was the last version of Ubuntu that ran smoothly on the laptop. I assume that if the problem is the kernel, then any recent distro will produce similar problems.

---

### Post by cantormath on 2007-05-24
> **tachum said:**
> Thanks for that. I might just go back to Dapper, which was the last version of Ubuntu that ran smoothly on the laptop. I assume that if the problem is the kernel, then any recent distro will produce similar problems.


Thats is why I still run dapper.  Good luck.

---

