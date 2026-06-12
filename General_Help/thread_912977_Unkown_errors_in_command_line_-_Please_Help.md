---
title: "Unkown errors in command line - Please Help"
date: 2008-09-07
forum: General Help
---

### Post by cbstryker on 2008-09-07
Hi everyone, every time I goto command line mode (CTRL + ALT + F2) I get errors that repeat continuously and spam the screen. (I go to the command line to install my nvidia drivers.) Here are the messages I get:

```
[ 223.941650] ata6: irq_stat 0x00000040, connection status changed
[ 223.941711] ata6: SError: {DevExch }
[ 232.795294] ata6: exception Emask 0x10 SAct 0x0 SErr 0x4000000 action 0xa frozen
```

And it just keeps repeating with the numbers in the [ 223.941711] part keep getting higher. The only thing that I can think of that I've changed recently was that I've added a 1000gb external hard drive through the eSata port. Other than that every thing has been the same.

Does anyone know remotely what this is?

---

### Post by cbstryker on 2008-09-07
****bump****

---

### Post by lintoon on 2008-09-07
A quick search on google brought this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/198871](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/198871)

I wonder if changing your bios setting for sata eill work.  Try toggling the ata or ahci setting.

---

### Post by cbstryker on 2008-09-08
Thanks, the AHCI setting seems to have done it.

---

