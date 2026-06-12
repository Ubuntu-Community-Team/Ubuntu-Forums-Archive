---
title: "Problem with installation amd driver"
date: 2015-04-18
forum: Hardware
---

### Post by abbobba on 2015-04-18
Hi 
I have a notebook with the intel hd 4600 and the amd hd 8750M. I show you the comand lspci
```
[COLOR=#555555][FONT=Monaco]00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]00:1c.1 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #2 (rev d5)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]00:1f.0 ISA bridge: Intel Corporation HM86 Express LPC Controller (rev 05)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]01:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Mars [Radeon HD 8670A/8670M/8750M] (rev ff)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]08:00.0 Network controller: Broadcom Corporation BCM43142 802.11b/g/n (rev 01)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]09:00.0 Ethernet controller: Qualcomm Atheros QCA8172 Fast Ethernet (rev 10)[/FONT][/COLOR]
```

I want to install the proprietary driver but, following this: [http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450) and other tutorial I stuck on
```
[COLOR=#555555][FONT=Monaco]sudo aticonfig --initial -f[/FONT][/COLOR]
```
because it return ```
[COLOR=#555555][FONT=Monaco] No supported adapters detected[/FONT][/COLOR]
```

I also tried to download the driver from amd's site and execute the *.run but also I stuck  [http://postimg.org/image/h43vhz1mb/](http://postimg.org/image/h43vhz1mb/)

P.s. I tried on ubuntu, xubuntu and mint

---

### Post by abbobba on 2015-04-19
up

---

### Post by rcgnaber on 2015-04-24
I have (almost) the same hardware and what works for me in 14.10 is the answer at this link: [http://askubuntu.com/questions/547387/cant-access-system-settings-or-catalyst](http://askubuntu.com/questions/547387/cant-access-system-settings-or-catalyst)

You can only do the purge and install steps before restarting.

---

### Post by abbobba2 on 2015-08-22
```
gianluca@G510:~$ sudo amdconfig --initialamdconfig: No supported adapters detected



```

nothing

---

