---
title: "Intel Corporation Centrino Wireless-N 1000 Not Finding my &quot;N&quot; network"
date: 2011-12-25
forum: Hardware
---

### Post by dmanges on 2011-12-25
I've searched through the forums & have been unable to find anything relevant to the Intel Corporation Centrino Wireless-N 1000. It appears as of 11.10, that the card has had no issues. Although my card connects fine to B/G networks, it doesn't find the "N" network. I've tested the network, my gnex connects fine, so does my fiance's MacBook. I'm running 11.10 64-bit & just want to be able to maximize my connectivity, any advice would be greatly appreciated. Here's my lspci:


00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation 5 Series/3400 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
03:00.0 Ethernet controller: Atheros Communications AR8151 v1.0 Gigabit Ethernet (rev c0)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)


Thanks in advance. Happy Holidays!

---

### Post by JCoop on 2011-12-26
I am not sure if this applies to you, but I have been researching an unrelated issue with an intel centrino 6150 N wireless card. Several of the posts I read dealt with having to disable the "N" functionality of certain intel cards in order to make them work at all. The command to disable the "N" feature of the card was:

cat /etc/modprobe.d/iwlagn.conf
options iwlagn 11n_disable50=1 11n_disable=1

The number one means it is turned off. If you change it to zero it should work. The problem is that it may cause the card to work improperly for some reason. This fix may have just been incorporated into the kernel by now and that may be why it isnt working. I hope this helps you solve your problem. Let me know if you have any other questions and I will try and locate those posts about that issue.

---

### Post by wildmanne39 on 2011-12-26
Hi, intel cards really do not work with N speeds in linux if you enable N speed it will most likely not connect or will have severe disconnects.
Thanks

---

### Post by dmanges on 2012-01-01
That's a shame... I never really bought into the Wireless-N speeds until I actually started using it. I looked in the location you provided & could not find the iwlagn.conf file. A full search provided no results. Thanks for your responses & suggestions, please let me know if you find anything else out, Happy New Year!

---

### Post by wildmanne39 on 2012-01-01
Hi, you did not find that file by JCoop because it is a file that you would create yourself using gedit, if you want to create it post back.
Thanks

---

