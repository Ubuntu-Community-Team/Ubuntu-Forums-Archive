---
title: "Computer Shuts Down When AC Adapter is Connected"
date: 2009-11-16
forum: Hardware
---

### Post by dyous87 on 2009-11-16
I have a Dell Vostro 1000 laptop. It has an AMD Athlon 64x2 with 4 gigs of RAM and it is running Ubuntu 9.10 x64. Everything is running flawlessly except one thing. 

If I plug the AC adapter in anytime before it gives me the 5 minute of battery life left warning, the computer will shutdown as if the battery is about to die. Even if the computer is 50% or 75% charged and I plug it in, the computer shuts down. 

This is really annoying because if I want to plug my laptop into the AC adapter, I have to wait till it is about to die to do so. Does anyone know what would cause this and how to stop it from happening.

Thanks in advance for all your help.

David

---

### Post by dyous87 on 2009-11-16
No I doubt it because right before I upgraded to 9.10 from 9.04 i didn't have this problem.

---

### Post by dyous87 on 2009-11-16
Bump...

---

### Post by BraedenNaylor on 2009-11-16
Well if it is ruled out that it is a hardware problem then it would be a bug with an Ubuntu package, something to do with power. File a bug report?

EDIT: Try booting into a live CD, 9.04 and / or 9.10, plug it in, see if it does the same thing.

---

### Post by dyous87 on 2009-11-16
I booted a 9.04 live CD and it doesn't have this issue although the 9.10 live cd does the same thing. I'm not sure what information I would need gathered to include in a big report.

David

---

### Post by dmizer on 2009-11-17
> **dyous87 said:**
> I booted a 9.04 live CD and it doesn't have this issue although the 9.10 live cd does the same thing. I'm not sure what information I would need gathered to include in a big report.

David

For how to file a bug report, take a look here: [http://kmandla.wordpress.com/2007/12/20/howto-file-a-bug-report-on-launchpad/](http://kmandla.wordpress.com/2007/12/20/howto-file-a-bug-report-on-launchpad/)

---

### Post by madengineer on 2009-11-17
Do you mean the 9.10 live cd behaves normally (no shutdown when AC connected) or reproduces the problem you have when booting from HD? If it behaves normally, it might be worth checking the power policy configuration, in case a configuration file left over from Jaunty got misinterpreted (a lot of my old config files on my desktop machine caused problems, finally leading me to create a new /home directory and start afresh). I'm not sure what the appropriate program would be on Ubuntu; on Kubuntu it's powerdevil, and can be accessed from System Settings.

---

