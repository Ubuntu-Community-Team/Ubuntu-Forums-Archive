---
title: "Wireless does not work on boot"
date: 2009-04-15
forum: Installation &amp; Upgrades
---

### Post by Jeffly777 on 2009-04-15
After monkeying around for hours I have my wireless working well on my Dell running Ubuntu 8.10.  It has the Broadcom BCM 4328 wireless chipset working with Broadcom STA and the networks configured through network manager.  

The problem is that the wireless will not work at all at startup.  I have to run a script that runs the commands:

sudo modprobe -r b43 b44 ssb wl
sudo modprobe wl
sudo modprobe b44
sudo /etc/init.d/networking restart

After this (and a delay) the wireless will start to work and ask me for my password.  Is there a way to configure my system so the wireless will work at boot?  Also, can I get the computer to stop asking me for the password to log into a wireless network, or would that be a bad idea?

Thanks.

---

