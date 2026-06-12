---
title: "pci problem"
date: 2016-06-01
forum: Hardware
---

### Post by guido96 on 2016-06-01
hello when i start my notebook appear on the screen this errors on pci bus. I've seen from terminal that pci bus is connected whit my graphic card (nvidia 920m). I upgrade the drivers but there are the errors yet. Someone can solve?
ps sorry for my poor english

---

### Post by Yellow Pasque on 2016-06-01
> **guido96 said:**
> I upgrade the drivers but there are the errors yet. 

Please give the output of the following commands:
```
uname -a
sudo modinfo nvidia | grep version
```

---

### Post by guido96 on 2016-06-02
Code:
guido@Xubuntu-16:~$ uname -a
Linux Xubuntu-16.10 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
guido@Xubuntu-16:~$ sudo modinfo nvidia | grep version
[sudo] password for guido: 
modinfo: ERROR: Module nvidia not found.

---

### Post by Yellow Pasque on 2016-06-02
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1521173](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1521173)

So, the conclusion of the bug report seems to be add pci=noaer to the boot line:
```
gksu mousepad /etc/default/grub
```

Change the following line:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
to:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=noaer"
```

Save and exit. Then run:
```
sudo update-grub
```

The messages should no longer appear once you reboot the system.

---

### Post by guido96 on 2016-06-03
thank you, solved:)

---

