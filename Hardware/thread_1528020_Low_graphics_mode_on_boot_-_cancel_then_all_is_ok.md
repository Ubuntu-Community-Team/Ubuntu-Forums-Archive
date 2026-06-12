---
title: "Low graphics mode on boot - cancel then all is ok?"
date: 2010-07-10
forum: Hardware
---

### Post by carlbeech on 2010-07-10
Hi Forum,

I installed 64bit Ubuntu 10.04 on my Asus X59GL laptop a little while ago, and all was fine, however, I started to get a message about starting in Low Graphics Mode and asking if I want to reconfigure every once in a while, now I get it every time...
I then press 'Cancel', and then everything starts ok.

I've no problems with the graphics, full screen, 3d etc are all working...

Looking in the logs (Xorg) I can see:

NVIDIA: could not open the device file /dev/nvidiactl (No such device or address).
(EE) Jul 10 07:22:59 NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
(EE) Jul 10 07:22:59 NVIDIA(0):     system's kernel log for additional error messages and
(EE) Jul 10 07:22:59 NVIDIA(0):     consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.

But I havn't spotted in the kernel log (/var/log/messages)

The nvidia chip is Nvidia GeForce 8200M G
The driver files installed are 'Nvidia-current' 195.36.24-0ubuntu1~10.04 and nvidia-settings 195.36.08-0ubuntu2

I always accept the system updates so these should be current....

Any ideas anyone - it doesn't stop my machine, but is pretty annoying...

Many thanks in advance

Carl.

---

