---
title: "How do I boot via LAN?"
date: 2009-06-18
forum: Installation &amp; Upgrades
---

### Post by running_rabbit07 on 2009-06-18
I have an old laptop that is running MS 2000 pro, I want 2000 to go away and to load Xubuntu because it uses the least resources. However the CDROM drive is not usable. I have an external CDROM drive but I can not set the BIOS to boot from it. 

I believe that I am left with booting it from another PC. 

I am running Ubuntu 9.04 from the desktop that I want to use to load the lappy. Is it possible to do a network boot and if so how do I do it?

I searched for network booting within the forum and didn't see anything helpful.

---

### Post by lykwydchykyn on 2009-06-18
It's possible, but it depends on your laptop hardware somewhat.  Basically, it needs to have a PXE-capable network adapter in it.  Some older devices use a different network boot protocol called RPL (which I've never gotten to work with my linux boot server) and some don't have network boot capabilities at all.

This is an old tutorial on it, but it should work if you just replace the release names:

[http://www.howtoforge.com/ubuntu_pxe_install_server_p2](http://www.howtoforge.com/ubuntu_pxe_install_server_p2)

It tells you how to set up a multi-boot to install many distros, but of course you can stop after the bit about Ubuntu.

---

### Post by running_rabbit07 on 2009-06-18
Thanx for the help. I tried a different ISO image than previously and the people that wrote the code did a great job because the disk forced the system to load from the external cd drive and it is currently partitioning to install. Again, thank you for you help!

And now I can say I have a PC with no Microsoft on it. Thanx to the people who build Debian and Ubuntu!

---

