---
title: "Unrecoverable Freeze/Suspend on xscreensaver after 11.10 upgrade"
date: 2012-03-19
forum: Hardware
---

### Post by nalgarryn on 2012-03-19
As of last week I was still running 10.04 (Lucid Lynx) and upgraded to 10.10, 11.04, and then 11.10 all in sequence in the last week through the update manager. Now my computer, when left unattended, dies unrecoverably.

I did have xscreensaver installed and it still works. (BSOD etc.) I adjusted my power settings to merely blank the screen and shutdown at critical power, without using either suspend. However I think the options now available are less than I had last week with Lucid. I think part of the problem is that the whole system is chugging. I run at 99-100% CPU constantly and I'm not sure why. I have conky installed and am at ~60% RAM usage but 100% CPU.

Attempts to resolve this issue are welcome; hardware to follow:

Acer Aspire 5315
1GB RAM
Intel Celeron CPU 530 @ 1.73 GHz
Intel G965 VGA
Intel 82801H (ICH8) Audio
NetLink/Broadcomm Ethernet PCI
Atheros A5001 Wireless Adapter
Intel 82801 SATA
Ubuntu 11.10 (32 bit)
Linux 3.0.0-16-generic kernel

I think that might be all the info...

---

### Post by nalgarryn on 2012-03-19
I just tried a:

sudo apt-get remove gnome-screensaver

I'm not sure if xscreensaver (which I had installed before upgrading) is causing any conflicts with gnome-screensaver which is apparently installed by default in 11.10.


~~~~~~~~~~~~~~~

Now I really did it. I was messing around in Compiz settings and enabled a couple of the "cube" settings and it required me to disable the "wall" settings. I did so, but now my dash and title-bar have disappeared. Any ideas on where to edit a .conf file to get them back, or how I can undo that from a CLI?

Thanks in advance!


~~~~~~~~~~~~~~~

[EDIT]

I discovered a website that details how common it is for people to fubar their 11.10 UI through Compiz settings. It luckily also detailed a way back, which I have done. I've also uninstalled Gnome-screensaver and installed Xscreensaver. I'll continue tinkering and mark this as solved.

---

