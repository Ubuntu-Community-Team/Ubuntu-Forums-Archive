---
title: "Primera LX810 color label printer driver"
date: 2016-06-05
forum: Hardware
---

### Post by John_Eggertsen on 2016-06-05
I want to completely migrate from Window to Ubuntu 14.04 LTS.  The last thing on my list is the ability to use the Primera LX810 color label printer.  The printer uses a USB connection.

I have a CD with both Mac and Windows drivers.  I contacted Primera for Linux drivers for the printer and was told that the only drivers that they have are for either Mac or Windows.  I attempted to add the printer but it is not in the printer manufacturer is not listed on Ubuntu. I also looked at [www.openprinting.org]("http://www.openprinting.org") for a driver, they didn't have any listed for the manufacturer or the printer.

I attempted to extract a driver from the Mac dmg file using dmg2img without any luck.

I am hoping that someone either has found an existing driver that will work or has some suggestions of drivers that I might try to use.  I am open to any ideas or recommendations.

Thanks in advance.

John

---

### Post by DuckHook on 2016-06-06
Welcome to the forums, John_Eggertsen,

I'm afraid that my Google-Fu is no better than yours on this one and such a driver probably doesn't exist. In cases such as yours, there's typically three options:

[LIST=1]
[*]Leave Windows on your machine as a dual boot (guaranteed to work but clumsy, untidy, inconvenient and wasteful of HDD),
[*]Try running the Windows driver with WINE (low probability of success and fraught with much weeping and gnashing of teeth),
[*]Run Windows inside a virtual machine and install the driver to that (the most "elegant" solution, but difficult on older slower HW).
[/LIST]
If your HW is relatively new and decently powerful, I would recommend option #3. It won't require you to reboot just to use a printer or to wrestle with the complexities of WINE. It has the added advantage that any old Windows apps that you belatedly discover to be necessary can also run in the VM. It's as close we get to having the best of both worlds.

---

