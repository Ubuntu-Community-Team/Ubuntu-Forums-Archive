---
title: "i7-1065G7 with Dell WD19TB : It cannot detect second monitor"
date: 2019-12-12
forum: Hardware
---

### Post by siblue2 on 2019-12-12
Hi.

I'm using XPS 2in1 7390 (Icelake: i7-1065G7 - Gen 11 GPU) with WD19TB (thunderbolt 3 docking station).

It's working well the extend display while the two monitors are being detected fully .

But Ubuntu 19.10 cannot detect the second monitor and display as only mirror mode.

The drivers are latest.


> 
$ sudo lspci
00:00.0 Host bridge: Intel Corporation Device 8a12 (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Device 8a52 (rev 07)
00:04.0 Signal processing controller: Intel Corporation Device 8a03 (rev 03)
00:05.0 Multimedia controller: Intel Corporation Device 8a19 (rev 03)
00:07.0 PCI bridge: Intel Corporation Device 8a1d (rev 03)
00:07.2 PCI bridge: Intel Corporation Device 8a21 (rev 03)
00:0d.0 USB controller: Intel Corporation Device 8a13 (rev 03)
00:0d.2 System peripheral: Intel Corporation Device 8a17 (rev 03)
00:0d.3 System peripheral: Intel Corporation Device 8a0d (rev 03)
00:12.0 Serial controller: Intel Corporation Device 34fc (rev 30)
00:14.0 USB controller: Intel Corporation Ice Lake-LP USB 3.1 xHCI Host Controller (rev 30)
00:14.2 RAM memory: Intel Corporation Device 34ef (rev 30)
00:14.3 Network controller: Intel Corporation Device 34f0 (rev 30)
00:15.0 Serial bus controller [0c80]: Intel Corporation Ice Lake-LP Serial IO I2C Controller #0 (rev 30)
00:15.1 Serial bus controller [0c80]: Intel Corporation Ice Lake-LP Serial IO I2C Controller #1 (rev 30)
00:15.3 Serial bus controller [0c80]: Intel Corporation Ice Lake-LP Serial IO I2C Controller #3 (rev 30)
00:16.0 Communication controller: Intel Corporation Device 34e0 (rev 30)
00:1d.0 PCI bridge: Intel Corporation Ice Lake-LP PCI Express Root Port #9 (rev 30)
00:1d.7 PCI bridge: Intel Corporation Device 34b7 (rev 30)
00:1f.0 ISA bridge: Intel Corporation Ice Lake-LP LPC Controller (rev 30)
00:1f.3 Audio device: Intel Corporation Device 34c8 (rev 30)
00:1f.4 SMBus: Intel Corporation Ice Lake-LP SMBus Controller (rev 30)
00:1f.5 Serial bus controller [0c80]: Intel Corporation Ice Lake-LP SPI Controller (rev 30)
2c:00.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge DD 2018] (rev 06)
2d:02.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge DD 2018] (rev 06)
2d:04.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge DD 2018] (rev 06)
2e:00.0 USB controller: Intel Corporation JHL7540 Thunderbolt 3 USB Controller [Titan Ridge DD 2018] (rev 06)
59:00.0 Non-Volatile memory controller: Device 1e0f:0001
5a:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS525A PCI Express Card Reader (rev 01)


Please let me know your idea.

Thanks in advance,

---

### Post by mörgæs on 2019-12-14
> **siblue2 said:**
> 
The drivers are latest.


Is the BIOS too?

---

### Post by oldfred on 2019-12-14
[SOLVED] dock Dell TB16 does not work with XPS 13  - needed Firmware updates
[https://ubuntuforums.org/showthread.php?t=2431141](https://ubuntuforums.org/showthread.php?t=2431141)

Although this user seems to have slightly different model & updated firmware & still issues.
[https://ubuntuforums.org/showthread.php?t=2433026](https://ubuntuforums.org/showthread.php?t=2433026)

---

### Post by siblue2 on 2019-12-27
Sure. The BIOS is latest...

---

### Post by aj-johnson-sflo on 2020-01-03
I have the same setup, XPS 7390 with the WD19TB dock, except I'm on 18.04.3 LTS. I did get the dock working finally and it will power one external monitor nicely at 4k through the dock, either DisplayPort or HDMI. But if I attempt to run two external monitors through the dock, no matter what combination, it does not work.

When you plug both external monitors in, does your laptop's native display still work? What does xrandr look like when you have both plugged in?

---

