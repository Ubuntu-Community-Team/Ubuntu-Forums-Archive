---
title: "Boot up problem"
date: 2008-10-04
forum: General Help
---

### Post by capo1949 on 2008-10-04
Hi
Can you please advise where I can change this function so the system boots into ubuntu and not MythTV.

I expected to find an entry in etc/inittab not used now.
I ave since discovered that run level definitions are defined in /etc/init.d and ubuntu boots into run level 2 by defaut in rc2,d directories in /etc
I don't understand this enough to make the necessary changes could you tell me where make tese changes so it boots to ubuntu and not mythtv

Thanks in anticipation
Graham

---

### Post by Ryadt on 2008-10-04
Can you post the output of```
cat /boot/grub/menu.lst
```

---

### Post by capo1949 on 2008-10-05
Hi Ryadt
Thanks for your response, I have resolvd the problem and found it tobe finger problem on log in Duh
Thanks again for your interet
Graham

---

