---
title: "[SOLVED] Need emergency restart from command line."
date: 2008-09-10
forum: General Help
---

### Post by enderal on 2008-09-10
Ubuntu is hanging up so I need to restart from the command line. How?


Thank you.

---

### Post by tuxxy on 2008-09-10
To power off;

```
shutdown -h now 
```

To restart the system;

```
shutdown -r now 
```

---

### Post by Sycron on 2008-09-10
For reboot you can simply use ```
sudo reboot
```

---

### Post by enderal on 2008-09-10
Thx much.

---

### Post by p_quarles on 2008-09-11
There's also:
```
sudo halt
```
Also useful is the fact that, on a physically present tty, you can hit ctrl-alt-del to reboot without password permissions. This will not work if X is running, so you would need to drop to the tty itself (not just the display manager) before doing this. 

The behavior of ctrl-alt-del can also be customized to use a different command if desired.

---

### Post by Shazaam on 2008-09-11
Also, during a complete lockup don't forget Raising Elephants!
Hold down the ALT+SysRq keys and type in...
```
reisub
```
[http://fosswire.com/2007/09/08/fix-a-frozen-system-with-the-magic-sysrq-keys/](http://fosswire.com/2007/09/08/fix-a-frozen-system-with-the-magic-sysrq-keys/)

---

### Post by Sycron on 2008-09-11
You can also do ```
sudo init 6
``` :D

---

