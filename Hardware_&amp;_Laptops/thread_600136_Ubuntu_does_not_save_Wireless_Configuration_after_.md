---
title: "Ubuntu does not save Wireless Configuration after Reboot"
date: 2007-11-01
forum: Hardware &amp; Laptops
---

### Post by SideWinder717 on 2007-11-01
I am new to Linux

I am using Ubuntu 7.10 on my Dell Inspiron 1200.  I have a broadcom chipset wireless card.  I am able to install my card using ndiswrapper 1.48 and can successfully connect to a wireless network.

After I reboot the computer, my wireless connection is no longer connected and the power light on my wireless card is off.  I have to remove the driver of the wireless card from ndiswrapper and reapply for the card to activate.  From there, I can once again use my wireless.

Is there a way to keep my wireless to launch automatically when system starts?

---

### Post by JC Casiano on 2007-11-02
Do you really have to remove the driver, or is this just one of the things you tried that seemed to work?  If you type "modprobe ndiswrapper" at a command line does the adapter become active (you may have to "sudo" this)?

Instructions I found online say that if you add the line "ndiswrapper" to the /etc/modules file you can get ndiswrapper to load automatically.  I did this to get my Airlink 101 AWLL6080 USB adapter to load, and it's worked consistently.

---

### Post by SideWinder717 on 2007-11-02
Removing the driver and reinstalling was something that was working, don't know if it was completely necessary.

Yes, modifying the /etc/modules file worked for me and ndiswrapper loads my wireless driver everytime I boot.  Thank you!

---

