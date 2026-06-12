---
title: "Dell Inspiron 5150 Freezes intermittently"
date: 2007-05-17
forum: Hardware &amp; Laptops
---

### Post by Hisstareia on 2007-05-17
Just installed Ubuntu Edgy on Inspiron 5150 without much hitch (except for a wireless issue I was able to solve with ndiswrapper). However, I've noticed that when using it it will freeze up around 30 minutes after startup. It's a total freeze; I cannot use the mousepad, ctrl-alt-backspace or anything else but hold down the power button. I think it might have something to do with the mounting of USB devices, but that's just a hunch. Everything's standard except for an ndiswrapper for my wlan. Syslog, hardware, and other system information is available if I need to post it. Please help as I really want to love ubuntu, but between this and my wireless dropouts it's getting difficult ](*,)

UPDATE

Below is the syslog that popped up during a session where I was actually able to have the computer recover from the freeze. Hope it helps:

Message from syslogd@hisstareia-laptop at Fri May 18 10:35:28 2007 ...
hisstareia-laptop kernel: [  485.436000] Uhhuh. NMI received for unknown reason b1 on CPU 0.

Message from syslogd@hisstareia-laptop at Fri May 18 10:35:28 2007 ...
hisstareia-laptop kernel: [  485.436000] You have some hardware problem, likely on the PCI bus.

Message from syslogd@hisstareia-laptop at Fri May 18 10:35:29 2007 ...
hisstareia-laptop kernel: [  485.436000] Dazed and confused, but trying to continue

---

