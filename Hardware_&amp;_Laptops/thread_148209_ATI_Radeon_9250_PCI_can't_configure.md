---
title: "ATI Radeon 9250 PCI can't configure"
date: 2006-03-21
forum: Hardware &amp; Laptops
---

### Post by falloutvictim on 2006-03-21
This just started on a fresh install after XP hosed. 

System:
MB - soyo kt400 ultra 
Processor - xp2400 
graphics card - ati radeon 9250 pci 256 
memory - 512 RAM

I first installed XP, which I couldn't boot into after I installed breezy. So, I wiped the hard drive and started over without XP. So Breezy was running fine for a full day, then the monitor just shut off. The system was still running fine! My music was playing perfectly. So I shut down manually since there was no response from any key combinations. Restarted to the strangest pixelated screen I've ever seen, with huge green globs all over the place on the terminal start up screens. So I thought there was a video problem, and proceeded to install the ATI drivers three different ways (via the automated install ATI offers (ICK!), via a line by line instructional tour on this forum (see radeon 9800 install), and via an fglrxconfig and some manual xorg.conf editing). With new drivers, I could get all the way into Gnome, but it would freeze, either opening synaptic, or terminal, or on log out (which were the only apps I tried). With the fglrx installed and edited in the xorgconfig file, it would freeze when I logged in, and it would only show half the Gnome desktop.
The drivers I tried in the xorg.conf file were "fglrx", "radeon" and "ati".  The ati driver will at least let me log into Gnome, but will freeze after I've dillied with a couple of applications.
So that's where I am. I'm having a hard time doing anything without a total lock up.
I'm trying to get a nice editing system going with cinelerra, dvgrab, etc.  Everything was working fine until the fresh install.
Any ideas would be most appreciated.
Thanks

---

### Post by falloutvictim on 2006-03-21
I fixed it.. nm... 
echo fglrx | sudo tee -q /etc/modules
sudo depmod -a ; sudo modprobe fglrx

that's all it needed.

---

