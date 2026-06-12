---
title: "[SOLVED] Permanently apply Powertop power savings"
date: 2008-09-17
forum: Hardware
---

### Post by rockin_goliath on 2008-09-17
I love the power savings that I can get with Powertop, but every time I restart my computer, the power saving changes get reverted back. Does anyone know of a way that I can have the changes apply permanently, or better yet, only when I disconnect my laptop from AC power?

---

### Post by bingoUV on 2008-09-17
Do you run some commands to apply Powertop power savings? If yes, put those commands in /etc/rc.local. Thus, those commands will get executed everytime you start the computer and hence enable power savings.

---

### Post by rockin_goliath on 2008-09-19
Holy crap! You totally rule! That saves me at least 30 minutes of battery life!

---

### Post by eldragon on 2008-09-19
> **rockin_goliath said:**
> Holy crap! You totally rule! That saves me at least 30 minutes of battery life!

and wait till newer kernels appear. intrepid will include the aspm patch which makes the pci-e bus save lots of power on battery :D

---

