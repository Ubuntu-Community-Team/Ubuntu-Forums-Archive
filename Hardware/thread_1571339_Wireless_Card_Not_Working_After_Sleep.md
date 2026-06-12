---
title: "Wireless Card Not Working After Sleep"
date: 2010-09-09
forum: Hardware
---

### Post by jakewalker on 2010-09-09
Hi,

I am running Ubuntu 10.06 on a Toshiba laptop.  Everything has been working fantastically, except that when I return from sleep, my wireless is shown as disconnected and it cannot again reconnect or see any wireless networks.  A reboot solves the problem.

If it helps, I'm using the ath9k driver.

Is there anything I can do (a script I can create or a command I can run) that will reset the wireless adapter after the computer returns from sleep that will allow me to reconnect without having to reboot the entire system?  

Any advice is appreciated.

---

### Post by Yellow Pasque on 2010-09-09
Hmm. I would try to unload and reload the kernel module, i.e:
```
sudo modprobe -r ath9k
sudo modprobe ath9k
```

---

### Post by deadvirus on 2011-08-17
> **Temüjin said:**
> Hmm. I would try to unload and reload the kernel module, i.e:
```
sudo modprobe -r ath9k
sudo modprobe ath9k
```

I have the same problem and I usually do this and it works. Isn't there any fix?

---

