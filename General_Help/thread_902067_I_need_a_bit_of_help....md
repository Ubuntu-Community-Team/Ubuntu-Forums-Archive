---
title: "I need a bit of help..."
date: 2008-08-27
forum: General Help
---

### Post by Biafore on 2008-08-27
Ok so I'm new to Ubuntu, and a couple days ago I installed it on my Toshiba Satellite A2000 laptop.

today I recieved this error ```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

when trying to access the synaptic manager.

Can anyone please help me in any way to fix my problem?

---

### Post by sisco311 on 2008-08-27
Close Synaptic, open a terminal (Applications->Accessories->Terminal)
and type:
```
sudo dpkg --configure -a
```press Enter, input your password and press Enter again.

---

### Post by Immolatus on 2008-08-27
It's telling you exactly what to do... well almost exactly.
Open a terminal and type:

sudo dpkg --configure -a

It will prompt you for your password, give it then press enter.

"dpkg" is part of the system that manages the addition and or removal of software. In this case, as is stated in the debug message, it has suffered an interruption for what ever reason and needs to be reset.That is what the above command is for. Think of it like clearing a logjam.

---

