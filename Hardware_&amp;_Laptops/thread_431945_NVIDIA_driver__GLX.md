---
title: "NVIDIA driver / GLX"
date: 2007-05-03
forum: Hardware &amp; Laptops
---

### Post by brehmium on 2007-05-03
Hi,

I'm running a GeForce4 MX 4000 and Ubuntu Feisty.
Exploiting the nvidia website and some other pages I figured out that the nvidia-glx driver should fit for me.
Sadly with either nvidia-glx* driver X doesn't start: The kernel module cannot be found...
Further I tried to use the driver from the nvidia-website (which ought to be the same). But here it is said that the driver cannot be compiled.
With the open NV driver I don't have GLX.

Is there anybody out there who could help me to fix this problem?
- Which is the right driver
- And what except [FONT="Courier New"]apt-get install[/FONT] and subsequently [FONT="Courier New"]nvidia-glx-config enable[/FONT] do I have to do in order to get my X run properly??


Thanks for ANY hints!

Cheers
Christian

---

### Post by jmgo on 2007-05-03
Yeah I have the same problem, the only difference is that my graphic card is geforce MX 440

Anyone?????:confused: :confused: :confused:

---

### Post by biffta on 2007-05-03
Hey guys I had the same problem and fixed it by completing all the parts of "Step 2" from the following guide, might find it works for you.
[URL="http://ubuntuforums.org/showthread.php?t=263851"]
http://ubuntuforums.org/showthread.php?t=263851[/URL]

---

### Post by tentwelveeight on 2007-05-03
I also tried all the difficult ways to get this exact card working, and finally I just uninstalled everything I had done and used Automatix. Worked like a charm! It's right there under NVIDIA drivers and I didn't have any problems at all. I highly recommend this method over all the root sudo sh terminal stuff. -joe

---

