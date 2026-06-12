---
title: "Question about switching video card"
date: 2015-01-08
forum: Hardware
---

### Post by palmgrower on 2015-01-08
14.04 LTS
Currently nVidia video card GT-240.
Before removing the nVidia card and installing a Radeon card HD 7970, should I install some Radeon software? Both cards are PCI-E type. Connection to 1080 TV is HDMI.

Problem: With Radeon in PCI-E slot, PC starts to the motherboard logo screen, then "no signal" appears on TV. Thanks.

---

### Post by QIII on 2015-01-08
Hello!

Uninstall the NVIDIA driver first.  Then shut down and remove the card.  Put the AMD/ATI card in.  Reboot and then install the fglrx driver (see the link in my signature).

I you have any problems, you know where to find us.

---

### Post by palmgrower on 2015-01-09
I did

sudo apt-get purge nvidia-settings
sudo apt-get autoremove

rebooted with Radeon/AMD card, pc booted to motherboard logo, UBUNTU screen with scrolling dots, and "no signal" message. Basically, no change. Anything else I can try? Thanks.

---

### Post by Yellow Pasque on 2015-01-09
You can try booting with 'nomodeset' in the kernel line. Hopefully, that will at least allow you to boot to the GUI.

I suspect you need a newer kernel and/or some updated components ( [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers) ) for the open-source radeon driver to work.

You can also try the proprietary driver. I'd probably install the latest Catalyst version from AMD rather than trying to use the one included with Ubuntu. [http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Before_you_start](http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Before_you_start)

---

