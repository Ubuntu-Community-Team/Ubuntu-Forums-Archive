---
title: "Need something that could keep my hdd active all the time."
date: 2009-05-16
forum: Hardware
---

### Post by trolleybus on 2009-05-16
Hello.

I have a laptop Dell Vostro 1310 with HDD Western Digital WD2500BEVT and using Ubuntu 9.04. I was suffering in fast increase of hard disk load cycle count when running on battery, so I applied an ugly fix and the problem has gone. But there is another. When Advanced Power Management (APM) is disabled, the hard disk temperature increases even when computer is idle. The temperature rises about to 46-47 degrees of celsius. When enabling APM using hdparm, the temperature will start decrease slowly but load cycle count then will start increasing. For example, in Windows Vista the APM seems to be disabled by default, temperature is around 38-40 C and load cycle count increases. But in Windows I'm using hdd SMART monitoring software called HD Tune which is refreshing smart values automatically after every 5 seconds thus keeping hard drive little bit active all the time and won't let load cycle count to increase. I need something similar for my Ubuntu that could keep hdd active, so I could enable APM to avoid temperature rising and get rid of increasing load cycle count as well. Is there any software that can keep hard drive active (maybe I can configure smartmontools somehow) or any script that could access disk about every 5-10 seconds?
Little bit long story but every suggestion would be appreciated. Thanks.

---

