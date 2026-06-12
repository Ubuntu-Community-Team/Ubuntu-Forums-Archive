---
title: "ubuntu 8.04 - Nvidia 9600GT and Samsung 2232bw"
date: 2008-06-17
forum: Hardware
---

### Post by cyber_brain_mfkg on 2008-06-17
hi all!
i've just installed ubuntu 8.04 on desktop machine on my work...

the configuration is:
Intel Core 2 Duo @ 3.00GHZ
4 GB DDR
Nvidia 9600GT 1GB
Samsung 2232BW Monitor...

The main problem is that during the installation screen goes to sleep and i have to restart it and start all over again!(mouse and keyboard doesn't work at all during the sleep)...I get black screen but system is active (i can say that using ssh).
Somehow i installed ubuntu but same problem occurred on installed system and i dont know what to do!
I've tried to change BIOS sleep settings to S1 (instead of S3) but same thing happened.
Any solution???

Thanx

---

### Post by phidia on 2008-06-17
Can you open another tty? Try pressing the Alt+Ctrl+F1 (F1-F7 any of those function keys) and logging in that way.

---

### Post by cyber_brain_mfkg on 2008-06-17
yes! i can change tty and i stop gdm, and after that everything is same.

---

### Post by phidia on 2008-06-17
> **cyber_brain_mfkg said:**
> yes! i can change tty and i stop gdm, and after that everything is same.

Just because you change tty doesn't mean gdm stops. Does one of the tty's bring you to your previous desktop? It should actually.
Try Alt+Ctrl+F7. Also if somehow your desktop has crashed/closed look at the output of dmesg and/or look at /var/log/ for other system output.

---

### Post by cyber_brain_mfkg on 2008-06-17
/etc/init.d/gdm stop

;)

i know how to stop gdm!i've installed new nvidia drivers...for now no problems...hope that this will solve issue.

if it fails i'll report!

peace

---

