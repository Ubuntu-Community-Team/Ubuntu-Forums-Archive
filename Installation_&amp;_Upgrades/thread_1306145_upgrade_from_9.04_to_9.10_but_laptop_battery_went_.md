---
title: "upgrade from 9.04 to 9.10 but laptop battery went off"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by Fressi on 2009-10-30
Hi, i was using upgrade manager to upgrade from 9.04 to 9.10, but then the battery went off and my laptop went into hibernation, when I plugged my laptop in, and turned it on, the upgrade manager was frozen white blank and didnt respond, so I restarted the laptop only to see the ubuntu sign and a loading bar underneath, and then come to a screen which says

mountall: symbol lookup error: mountall: undefined symbol: udev_monitor_filter_add_match_subsystem_devtype
init: mountall main process (766) terminated with status 127

and then I can type with my keyboard but esc repressents ^[

Then I downloaded ubuntu 9.10 from a torrent and wrote the .iso file to a cd and tried to boot the laptop from the cd but without a success

I reallly need help and would like to keep the files on the laptop

---

### Post by phillw on 2009-10-30
Ewww.... Nasty, but, hopefully, not fatal.

okies ...

1stly, check the cd and iso are okay....

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If it is unhappy with the cd - re-burn one, at about 4X speed

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Then check the laptop is set to boot from CD first in BIOS.

(when you turn it on, it'll say something like "Press F2 for BIOS")

Report back what you get

Regards,

Phill.

---

### Post by linux-hack on 2009-10-30
I really dont understand why do you upgrade a laptop without the electrical adaptor

---

### Post by phillw on 2009-10-30
An oversight, i guess. It's no different to some poor soul having a power outrage with a desktop ... these things happen.

It's the not having a backup that disappoints me :-(

Why, oh why will people NOT backup ?

Phill.

---

### Post by Fressi on 2009-10-30
Okey Phil, I've gone through these steps, but when I choose a temporary startup device, I can choose from 3 different boots: 

IDE ODD: HL-DT-St DVDRAM

SATA HDD: Fujitsu

PCI: LAN: Realtek Boot Agent

I choose the first one and recieve Grub Loading 1,5 

Some text about boot and then ubuntu sign and red line with yellow cursor moving around it, and then the same error message again, which disappears when i hit alt+f4, and end up with a black screen with a blinkin cursor on it.

The same thing happens when I choose option 2.

When I choose option 3, I get:

Intel UNDI, PXE-2.1 (build 082)
Copyright (c) 1997-2000 Intel Corporation

For Realtek RTL8139(X)/8130/810x PCI Fast Ethernet Controller v2.16 (041224)
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting PXE ROM

Intel UNDI, PXE-2.1 (build 082)
Copyright (c) 1997-2000 Intel Corporation

For Realtek RTL8139(X)/8130/810x PCI Fast Ethernet Controller v2.16 (041224)
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting PXE ROM
Operating System not found
_

and upon pressing alt+f4 I get to the same annoying error screen.

Now I think I've given up hope for getting my laptop running with my old files. How can I start using my laptop again?

Thanks for your help Phil

---

