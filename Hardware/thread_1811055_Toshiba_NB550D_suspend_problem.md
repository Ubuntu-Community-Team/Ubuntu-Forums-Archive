---
title: "Toshiba NB550D: suspend problem"
date: 2011-07-24
forum: Hardware
---

### Post by currydude on 2011-07-24
**_[SIZE="4"][COLOR="Red"]SOLUTION[/COLOR][/SIZE]_**
Upgrade to the latest version for the GPU (Catalyst 11.7). Full instructions here:
```
http://mygeekopinions.blogspot.com/2011/08/how-to-install-atiamd-catalyst-117.html
```

Thank You **PerlonKid**
[COLOR="White"]Hi guys,
I can't seem to properly resume from suspend on my netbook. When I do, and upon trying to resume, only find a black screen, cpu, harddrive and fans spin though.

Currently using Ubuntu 11.04 with Ubuntu 2.6.38-10-generic kernel. I am very new to Ubuntu, so please be nice :)

EDIT: I have Dual Boot (separate partitions) with Windows 7 32Bit, Ubuntu 11.04 is 64bit, could that be a problem?

I've read that the ati fusion c50 graphics drivers could be the problem?

[/COLOR]

---

### Post by PerlonKid on 2011-07-28
I have the exact same issue. I have dual boot of Window 7 and Linux Mint 11 and I see the same behaviour - can enter sleep/suspend with no problems but when I exit the netbook powers up but the screen remains black.

Not much help I know but at least you know it's not unique to your install!

---

### Post by currydude on 2011-07-29
It seems like a universal Linux problem (Most likely to do with the kernel - switch kernels has helped but problem still persist if I sleep/suspend for more than 2 minutes)

---

### Post by PerlonKid on 2011-08-06
Solved! You need to upgrade to the latest version for the GPU (Catalyst 11.7). Full instructions here:

[http://mygeekopinions.blogspot.com/2011/08/how-to-install-atiamd-catalyst-117.html](http://mygeekopinions.blogspot.com/2011/08/how-to-install-atiamd-catalyst-117.html)

---

### Post by currydude on 2011-08-07
> **PerlonKid said:**
> Solved! You need to upgrade to the latest version for the GPU (Catalyst 11.7). Full instructions here:

[http://mygeekopinions.blogspot.com/2011/08/how-to-install-atiamd-catalyst-117.html](http://mygeekopinions.blogspot.com/2011/08/how-to-install-atiamd-catalyst-117.html)

LOLS thanks for the reply. And dammit, just when I reformatting and went back to Windows 7 -.-"

I wonder if Wubi is good, feeling lazy repartitioning everything

---

### Post by Elza on 2011-09-30
I've done all you said on My Toshiba NB550D with 11.04 Ubuntu, but the screen still can't waken up from suspend mode. HELP.

---

