---
title: "Problem on samsung  notebook related to gddccontrol"
date: 2011-08-03
forum: Hardware
---

### Post by ranyac on 2011-08-03
Hello all,

I installed the gddccontrol and tried to launch it but I have always this message :

No monitor supporting DDC/CI available. If your graphics card needs it,  please check all the required kernel modules are loaded (i2c-dev, and  your framebuffer driver.)

Here is some info about my config :

> $ lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011]

$ uname -a
Linux ubuntu 2.6.32-33-generic #71-Ubuntu SMP Wed Jul 20 17:30:40 UTC 2011 i686 GNU/Linux


I tried to check the related posts in the forum but didn't find any solution.

Can you please help and please let me know if you need more info.

Regards,
Rany.

---

