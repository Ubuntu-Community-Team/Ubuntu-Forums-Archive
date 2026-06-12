---
title: "CUPS server error"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by atentik on 2009-11-02
After upgrading to Karmic, my printer was nowhere to be found. I tried adding a new printer System->Administration->Printing... but whenever I do, I get the following error: > 
**CUPS server error**
There was an error during the CUPS operation: 'client-error-bad-request'

I spent about 2 hours trying to figure out what the problem might be but to no avail. I reinstall cups but nothing... Any suggestions?

---

### Post by EJeanmaire on 2009-11-02
> **atentik said:**
> After upgrading to Karmic, my printer was nowhere to be found. I tried adding a new printer System->Administration->Printing... but whenever I do, I get the following error: 
I spent about 2 hours trying to figure out what the problem might be but to no avail. I reinstall cups but nothing... Any suggestions?

What if you purge CUPS instead of just apt-get install --reinstall?  Doing that will eliminate some of the configuration files which may be causing the issue.

---

### Post by atentik on 2009-11-02
> **EJeanmaire said:**
> What if you purge CUPS instead of just apt-get install --reinstall?  Doing that will eliminate some of the configuration files which may be causing the issue.
Thanks but how do I do that?
I tried > sudo apt-get install --purge cups . The error stopped popping but the icon for adding new printer is inactive. Any suggestions?

---

### Post by atentik on 2009-11-03
Nobody have any other suggestion?

---

### Post by atentik on 2009-11-04
This is terrible.... No Help at all?

---

### Post by grandtoubab on 2009-11-04
try to manage your printer completely with cups interface, in Firefox
[http://localhost:631/](http://localhost:631/)

if requested give your standard user/password to CUPS

Delete it, create it again, then verify it is activated and shared

more help at [http://www.cups.org/](http://www.cups.org/)

---

### Post by zob on 2009-11-04
Is your printer seen by lsusb?
```
lsusb
```

---

### Post by EJeanmaire on 2009-11-04
> **atentik said:**
> Thanks but how do I do that?
I tried . The error stopped popping but the icon for adding new printer is inactive. Any suggestions?

when CUPS is installed, type 'sudo apt-get purge cups'

---

### Post by atentik on 2009-11-04
> **zob said:**
> Is your printer seen by lsusb?
```
lsusb
```

Does not look like it. lsusb returns
> Bus 002 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Any idea how to get it to be detected?

---

### Post by atentik on 2009-11-04
> **EJeanmaire said:**
> when CUPS is installed, type 'sudo apt-get purge cups'

Did that but there seems to be no substantial result. Ubuntu is frustrating... if you know what I mean.

---

### Post by zob on 2009-11-04
I guess you'll have to reinstall cups after that one.

But nevermind I think there some strange problem in karmic, I've seen more people with usb hardware suddenly not showing up.
That's what were discussing in this thread. Come and join us.
[http://ubuntuforums.org/showthread.php?t=1311713](http://ubuntuforums.org/showthread.php?t=1311713)

---

### Post by zob on 2009-11-05
I have solved the problem I had with cups.

To get a faster boot with a dual-core machine I made a change in /etc/init.d/rc where i changed concurrency=none to concurrency=shell.
Setting it back to concurrency=none solved this problem and another problem I had with Grub.

---

### Post by atentik on 2009-11-08
> **zob said:**
> I have solved the problem I had with cups.

To get a faster boot with a dual-core machine I made a change in /etc/init.d/rc where i changed concurrency=none to concurrency=shell.
Setting it back to concurrency=none solved this problem and another problem I had with Grub.

Did you restart the computer after changing concurrency=none to concurrency=shell then changing it back or what?

---

### Post by zob on 2009-11-08
No wait. It's no a question of changing it. It's a question of NOT changing it.

It had, in an attempt to make my computer boot faster, changed the concurrency to shell. That was the problem. If I had never done that, I wouldn't have had a problem. You see?

Now, in my case, changing it back to 'none' fixed it. So if you haven't ever changed yours, it won't help you changing it, and changing it back. It might only bring you trouble.

Leave the CONCURRENCY=none.

---

### Post by atentik on 2009-12-07
My problem is STILL not SOLVED. Anybody know why I kept on getting
> Request from "localhost" using invalid Host: field ""
.
This is annoying...

---

