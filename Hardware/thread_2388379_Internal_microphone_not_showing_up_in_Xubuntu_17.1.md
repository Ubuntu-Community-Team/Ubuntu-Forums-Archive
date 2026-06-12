---
title: "Internal microphone not showing up in Xubuntu 17.10"
date: 2018-04-01
forum: Hardware
---

### Post by jameskay on 2018-04-01
Hi,

I must have updated recently through terminal, but my internal mic is not recognized properly in my audio mixer (the lock button and mute audio are grayed out), and it's not working.

arecord -l gives me:
[INDENT]**** List of CAPTURE Hardware Devices ****[/INDENT]
[INDENT]card 0: PCH [HDA Intel PCH], device 0: ALC3253 Analog [ALC3253 Analog][/INDENT]
[INDENT]  Subdevices: 1/1[/INDENT]
[INDENT]  Subdevice #0: subdevice #0[/INDENT]

lspci gives me:
[INDENT]**** List of CAPTURE Hardware Devices ****[/INDENT]
[INDENT]card 0: PCH [HDA Intel PCH], device 0: ALC3253 Analog [ALC3253 Analog][/INDENT]
[INDENT]  Subdevices: 1/1[/INDENT]
[INDENT]  Subdevice #0: subdevice #0[/INDENT]
[INDENT]mike@mike-ThinkPad-X140e:~$ lspci[/INDENT]
[INDENT]00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers (rev 02)[/INDENT]
[INDENT]00:02.0 VGA compatible controller: Intel Corporation HD Graphics 620 (rev 02)[/INDENT]
[INDENT]00:04.0 Signal processing controller: Intel Corporation Skylake Processor Thermal Subsystem (rev 02)[/INDENT]
[INDENT]00:13.0 Non-VGA unclassified device: Intel Corporation Device 9d35 (rev 21)[/INDENT]
[INDENT]00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)[/INDENT]
[INDENT]00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)[/INDENT]
[INDENT]00:15.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #0 (rev 21)[/INDENT]
[INDENT]00:15.1 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #1 (rev 21)[/INDENT]
[INDENT]00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI #1 (rev 21)[/INDENT]
[INDENT]00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21)[/INDENT]
[INDENT]00:1c.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #5 (rev f1)[/INDENT]
[INDENT]00:1f.0 ISA bridge: Intel Corporation Sunrise Point-LP LPC Controller (rev 21)[/INDENT]
[INDENT]00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)[/INDENT]
[INDENT]00:1f.3 Audio device: Intel Corporation Device 9d71 (rev 21)[/INDENT]
[INDENT]00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)[/INDENT]
[INDENT]01:00.0 Network controller: Intel Corporation Wireless 3165 (rev 79)[/INDENT]

I'm running Xubuntu 17.10.  Does anyone know what could be the problem?

Thanks,

James

---

### Post by Yellow Pasque on 2018-04-02
So it worked before you updated?
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

