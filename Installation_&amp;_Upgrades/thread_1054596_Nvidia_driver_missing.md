---
title: "Nvidia driver missing?"
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by Stolea on 2009-01-29
I just ran the automatic daily update. I now have a new (Ubuntu 8.04.2, kernel 2.6.24-23-generic) kernel. When I restarted my system I was greeted with the white screen of death. The pointer and sound were working, but my desktop had gone missing.
I managed to Ctrl_Alt-F1 at the next boot and through the options restore the desktop.
However, now I have the default Nvidia driver and only the default display, i.e. no enhancements possible. The "System/Hardware Drivers" box shows no installed drivers, where in my previous setup it did.
My question of the day: How do get my display drivers back????

---

### Post by Stolea on 2009-01-30
Anyone with any ideas? Please.....

---

### Post by gtdaqua on 2009-01-30
```

sudo apt-get install nvidia-glx-180

```

That will install the nvidia 180.xx drivers. Use 173 or 96 in place of 180 for proper version of your card.

---

### Post by Crafty Kisses on 2009-01-30
What NVIDIA card do you have?

---

### Post by Stolea on 2009-01-30
Thanks,
After checking on my hardware, I discovered that this computer has a ATI Raedon 9550 card. For some obscure reason it was telling me that it was Nvidia. Go figure that one out.
I have since installed the ATI driver and everything is happy again.
Cheers!

---

