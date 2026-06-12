---
title: "How to install SIS video card in Ubuntu?"
date: 2011-01-11
forum: Hardware
---

### Post by crixtiano on 2011-01-11
Hi,

I have an Acer notebook with AMD Turion 64 bit, installed Linux Ubuntu LTS 10.04.1.

I'm having a problem properly configure the video driver.

Ubuntu works correctly only in graphics mode (GDM). When I opt for an access terminal in text mode (CTRL-ALT-F1 to CTRL-ALT-F6) the screen is misconfigured, showing only about 25% of the screen (please, [ CLICK HERE see the screenshoot]("http://www.engehouse.com.br/temp/screenshoot_shell.jpg")). 

Also, I can not use the "Visual Effects" in graphical mode.

Please could someone give me a idea how to properly install the video driver for my card?

This is my video card:
```

$ lspci | grep VGA
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

$ lspci -n | grep 01:00.0
01:00.0 0300: 1039:6330
```

So, what do I have to do to fix the problem in terminal?

Thank you!

Cristiano

---

