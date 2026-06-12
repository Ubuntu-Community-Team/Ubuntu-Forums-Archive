---
title: "ASUS GU501GM (Zephyrus) Elantech touchpad troubleshooting"
date: 2018-05-15
forum: Hardware
---

### Post by wereturtle on 2018-05-15
Hi all,

I recently [submitted a bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1770862") against my touchpad for my new ASUS laptop, which appears to have an Elantech touchpad, ELAN1201 to be precise.  It is sadly not being detected in Ubuntu 18.04 with kernel 4.15, nor with the newer mainline kernel 4.16.7.  (I couldn't get X to even start with later mainline kernels.)  I've also contacted the Kernel maintainer for the touchpad drivers, per the Kernel bug submission process.  However, I was wondering if anyone here might be able to help me troubleshoot further?  You can see all my dmesg, "xinput list", Xorg.0.log, etc. outputs attached in the bug report I linked to.  Sadly, it doesn't look like there's a lot useful in there.

I was wondering if the root issue is the Fn+F10 keyboard shortcut, which is to enable/disable the touchpad.  I understand from my previous Internet searches that if the laptop starts up in Linux with the touchpad "off" according to the BIOS/keyboard, and if the keyboard's Fn shortcut to enable it doesn't work, then xinput won't detect the touchpad at all.

I've tried quite a few boot parameters.  Various combinations of i8042.reset, i8042.nomux, i8042.nopnp, and i8042.noloop.  Also I've tried psmouse.proto=bare, acpi_osi=! with acpi_osi=(Linux | Windows 2009 | windows 2012).  Finally, I've tried blacklisting i2c_hid and multitouch_hid (one at a time, of course).

Any other ideas?  Also, has anyone else had better luck with a full Zephyrus M?  (I stress the "M" model, as this one has a normal touchpad at the bottom of the laptop.)  Mine is the Best Buy exclusive, which is basically the Zephyrus M with a GTX 1060 and no flap at the bottom for airflow.  However, just because they appear the same doesn't mean they aren't using different touchpads.  I'd be willing to take this one back and pay more for a working touchpad if anyone can confirm the the Zephyrus M's touchpad does, indeed, work in Linux.

FYI, I also did try Manjaro in the hopes of having better luck installing newer kernels (particularly the 4.17 release candidates), but the install ISO comes with kernel 4.14, which doesn't work with my WiFi card.  How ironic that Bionic Beaver has a newer kernel than the rolling release!  Oh well, maybe in a few months.

Thanks in advance for your ideas.  I'll try anything.  ANYTHING.  It's a wonderful touchpad...in Windows, anyway.

---

