---
title: "Hald stopped working yesterday"
date: 2010-05-19
forum: Hardware
---

### Post by Skildron on 2010-05-19
Hello!

I have got a very strange problem: Starting yesterday in the afternoon, hald quit working on my Acer Extensa 5635Z Laptop with Kubunt Karmic Koala 32bit installed. It worked flawlessly beforehand. The last thing I remember doing before this problem occured was copying a large directory (>40G) from my server over to my laptop via a nfs mount. During this process, my wlan connection somehow got disconnected and the copying process hung. I rebooted my laptop to get rid of the stale mount that blocked my system. Afterwards, and ever since, hald ends with SIGSEGV on bootup, so that no login is possible because xorg does not recognize my touch pad and keyboard. Only way to login was via ssh to do some diagnostics. The really wierd thing is, when I am logged in via ssh and do "/usr/sbin/hald --daemon=yes", then hald starts just fine. If i try "initctl start hal" or "invoke-rc.d hal start", then hald crashes. My google searches did not result in anything helpfull - apt-get --reinstall install hal (and connected packages) did not help.

Perhaps someone here is able to shed some light on this

Greetings
Thorsten aka Skildron

---

### Post by Skildron on 2010-05-19
Addition to my error description: I did an strace both when hald crashed an when it started successfully. Perhaps someone can make anything out of it.

[http://www.mueller-kleinheinz.de/hald/hald-crash.txt](http://www.mueller-kleinheinz.de/hald/hald-crash.txt)
[http://www.mueller-kleinheinz.de/hald/hald-working.txt](http://www.mueller-kleinheinz.de/hald/hald-working.txt)

---

### Post by Skildron on 2010-05-20
Problem solved: I updated the usbids and pciids database files. After reverting to the versions shipped with Karmic in the respective packages (usbutils and pciutils), hald started working again.

---

