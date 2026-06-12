---
title: "Ubuntu Keeps Crashing"
date: 2008-11-07
forum: Hardware
---

### Post by yusuo85 on 2008-11-07
[CENTER]Im running ubuntu intrepid off a 1.7ghz laptop with just under 2gb ram and a 250gb hard drive attached via usb. Now my problem is that when ever I do anything that internet hungry e.g. torrents, large streamed videos or some flash games, the system just freaks.

My audio turns very internmitent and it cuts off the internet, refuses to load a web page or even try, cant even ping. This is usally solved by a restart but thats not a good option.
Would love to get this sorted as I hate resorting to Windows for things like that, any help appreciated [/CENTER]

---

### Post by phidia on 2008-11-07
As long as the system hasn't crashed or frozen you can open a terminal and type dmesg right after you experience the problems you described.

If the desktop isn't responsive you can open a tty by pressing Alt+Ctrl+F1 (F2-F7 also).

If there is no usable info from dmesg try looking at the /var/log/messages or other logfiles there. Hope that's useful.

---

