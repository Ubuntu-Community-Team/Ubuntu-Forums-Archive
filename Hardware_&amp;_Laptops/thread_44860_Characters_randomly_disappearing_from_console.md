---
title: "Characters randomly disappearing from console"
date: 2005-06-27
forum: Hardware &amp; Laptops
---

### Post by Red Sparrow on 2005-06-27
I have an old G4 iLamp that I'm converting into a web and mail server.  Because it has a built-in monitor, I set syslog-ng to display it's messages on a virtual console (/dev/tty8).  However, at seemingly random times, certain characters disappear from the console.  Usually, I'm left with just the hostname, the date, and a few characters from the timestamp.  If I hook up a keyboard and press a key, the characters come back.

I don't even know where to begin looking for the problem.  I suspect it may be due to some kernel option; perhaps due to a power management option.  Has anyone ever heard or seen this problem before?  What can I do to fix it?

Thanks,
(- Steve -)

---

### Post by Hex on 2005-06-28
[QUOTE=Red Sparrow]I have an old G4 iLamp that I'm converting into a web and mail server.  Because it has a built-in monitor, I set syslog-ng to display it's messages on a virtual console (/dev/tty8).  However, at seemingly random times, certain characters disappear from the console.  Usually, I'm left with just the hostname, the date, and a few characters from the timestamp.  If I hook up a keyboard and press a key, the characters come back.

I don't even know where to begin looking for the problem.  I suspect it may be due to some kernel option; perhaps due to a power management option.  Has anyone ever heard or seen this problem before?  What can I do to fix it?

Thanks,
(- Steve -)[/QUOTE]
 It seems like a video driver problem to me.

---

### Post by Red Sparrow on 2005-06-28
Yeah, I thought about that, too.  I've lost the specs to this machine, but I'm fairly sure the machine has an Nvidia GeForce 2.  However, I discovered today that if I log in on the console, I can let it sit for as long as I want and I don't have the same problem.  If it was a kernel config or video driver problem, wouldn't it occur on all the virtual consoles?

(- Steve -)

---

