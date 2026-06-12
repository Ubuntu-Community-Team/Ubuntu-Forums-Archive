---
title: "Need help with Moschip"
date: 2009-02-13
forum: Installation &amp; Upgrades
---

### Post by catdeerduck on 2009-02-13
Guys i need help. Im a new to Ubuntu, i've only been using it for 5 days now and i think its way better then Windows Vista already its way stable. Ok back to my problem.... I need to install this to my computer (its for my homework). Its a Driver but im just not able to install it
heres the link for the driver i need help on
[http://driverscollection.com/?H=MCS7703&By=Moschip](http://driverscollection.com/?H=MCS7703&By=Moschip)
also im using Ubuntu Intrepid 8.10

---

### Post by lemming465 on 2009-02-14
Um, looks like MCS7703 is a USB-to-serial converter.  Unlike unsupported network chips, where ndiswrapper can let windows drivers run in a Linux kernel context, I'm not aware of any windows USB driver emulation support in Linux.

However, there is a good chance that your serial device will just show up connected to /dev/ttyUSB0, unless it got pirated away by mistaken braille terminal support. You probably have to install "cu" or "kermit" or something to talk to it.

If you run *egrep -i 'usb.*serial' /var/log/dmesg* what messages, if any, turn up?  Does "lsusb" show your serial port device?

---

