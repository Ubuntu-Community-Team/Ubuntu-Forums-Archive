---
title: "Network Card Help"
date: 2005-01-24
forum: Installation &amp; Upgrades
---

### Post by Enzo386 on 2005-01-24
Ok i got this PC from somebody who upgraded there PC to a new one, and it's a 700  Mhz Pentium 3 with 256 Megs of ram, Ethernet, ATI Rage 128 Pro, and integrated sound. Anyways, when i go to install ubuntu, all goes well until it says it can't detect my ethernet card. I know it's compatible because it works under the live CD, but before i go ahead and dual boot ubuntu and XP on this machine, i wanted to make sure it would work after the install if it didn't detect it during the post-install process.

---

### Post by BORTKOMMEN on 2005-01-24
I am going to install Ubuntu but have not done it yet, but I have had similar problems connecting to the internet with other distributions. I installed Fedora Core 3, Suse 9.2 and could not connect to internet, on the other hand there were no problems with Suse 9.0 and Debian stable.
I believe it depends on the new kernel 2.6, that does´nt support certain network cards for example AMD Homebased pc adapter.
Those distributions I can connect with are based on kernel 2.4. I was not really sure about it so I tried with Knoppix version 3.7 and booted from the CD. With the default boot (kernel 2.4) I could access internet automatically. But then, when I used the boot option with kernel 2.6  I could not access internet. I am almost sure the problem is in the new kernel.

You can download Knoppix 3.7 and try those two boot-options.
Please let me know what results you get and what your network card is.
If it depends on the kernel we must do something to solve this.

---

