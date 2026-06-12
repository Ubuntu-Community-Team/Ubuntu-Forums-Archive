---
title: "XP-Kubuntu Dual boot"
date: 2008-08-03
forum: General Help
---

### Post by Cinjo on 2008-08-03
Hey I used kubuntu on this computer until I got a new hard drive and bought XP I installed XP onto the new hard drive and set the old one to be the slave as it was smaller I then went to My Computer->Properties->Advanced->Startup and Recovery->Settings->Clicked the Edit button and got my start up options file which I edited to look like this
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
D:\="kubuntu" 
```
When I start up my computer it gives me the option of Windows XP or kubuntu but when I click on kubuntu it just starts the boot process over again and goes back to the same selection screen until I select XP then it starts up properly. Anyone have any idea how to fix this?

---

### Post by logos34 on 2008-08-03
here try **Wingrub**:

[http://users.bigpond.net.au/hermanzone/p9.html](http://users.bigpond.net.au/hermanzone/p9.html)

---

