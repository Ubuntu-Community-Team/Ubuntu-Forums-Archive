---
title: "Ubuntu is unable to detect my GPU"
date: 2020-05-10
forum: Hardware
---

### Post by enon97 on 2020-05-10
Hello,

I have an MSI laptop which was working fine with Ubuntu 18, but I decided to upgrade. It has one of these dual graphics setups, which and Intel HD 630 and a NVIDIA GTX 1060 6GB. On Ubuntu 18, I simply get the NVIDIA GPU to work by selecting its drivers on the "Additional Drivers" tab under "Software and Updates", but on this version of Ubuntu, my GPU doesn't appear there any more.

Also, if I type this in the console: [COLOR=#212529][FONT=Inconsolata]$ lspci | grep -i --color 'vga\|3d\|2d'
[/FONT][/COLOR]
This is the only line I get: 
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 630 (rev 04)

Just in case, my laptop model is this: [https://es.msi.com/Laptop/GL72VR-7RFX](https://es.msi.com/Laptop/GL72VR-7RFX)

Any help would be appreciated.

Thanks.

Edit: I forgot to say that I also have Windows on dual boot and the GPU works perfectly fine there. Also, it is not disabled on the BIOS or something like that. I don't think that is even possible on my BIOS either.

---

### Post by collin80 on 2020-05-11
This same thing happened to me. Except that I was on Ubuntu 19.10 and working perfectly fine. I could either enable the nvidia card or disable it and use just the intel built-in and both worked fine. Now, like you, on Ubuntu 20.04 the nvidia card does not even show up with lspci or lshw. It's just plain missing. And, like you, I can dual boot and the nvidia card is found in Windows and works perfectly fine. It's a problem in Ubuntu 20.04 but I don't know why. I've tried disabling secure boot, makes no difference. I've tried installing the 5.6 linux kernel found in the official ubuntu source. That doesn't fix it either. What's strange is that this doesn't seem to be a widely reported problem but a whole lot of people must be running into it - unless we're both doing something stupid or ran into a very obscure issue.

Here's the full lspci from my Acer Nitro laptop:

00:00.0 Host bridge: Intel Corporation 8th Gen Core 4-core Processor Host Bridge/DRAM Registers [Coffee Lake H] (rev 07)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16) (rev 07)
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 630 (Mobile)
00:08.0 System peripheral: Intel Corporation Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th/8th Gen Core Processor Gaussian Mixture Model
00:12.0 Signal processing controller: Intel Corporation Cannon Lake PCH Thermal Controller (rev 10)
00:14.0 USB controller: Intel Corporation Cannon Lake PCH USB 3.1 xHCI Host Controller (rev 10)
00:14.2 RAM memory: Intel Corporation Cannon Lake PCH Shared SRAM (rev 10)
00:14.3 Network controller: Intel Corporation Wireless-AC 9560 [Jefferson Peak] (rev 10)
00:15.0 Serial bus controller [0c80]: Intel Corporation Cannon Lake PCH Serial IO I2C Controller #0 (rev 10)
00:15.1 Serial bus controller [0c80]: Intel Corporation Cannon Lake PCH Serial IO I2C Controller #1 (rev 10)
00:16.0 Communication controller: Intel Corporation Cannon Lake PCH HECI Controller (rev 10)
00:17.0 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 10)
00:1d.0 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port #14 (rev f0)
00:1e.0 Communication controller: Intel Corporation Cannon Lake PCH Serial IO UART Host Controller (rev 10)
00:1f.0 ISA bridge: Intel Corporation HM470 Chipset LPC/eSPI Controller (rev 10)
00:1f.3 Audio device: Intel Corporation Cannon Lake PCH cAVS (rev 10)
00:1f.4 SMBus: Intel Corporation Cannon Lake PCH SMBus Controller (rev 10)
00:1f.5 Serial bus controller [0c80]: Intel Corporation Cannon Lake PCH SPI Controller (rev 10)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 25)

---

### Post by wildmanne39 on 2020-05-11
Hello collin80, please start your own thread if you need support for this issue so you and the OP of this thread can both get the individual help that you deserve plus it gets confusing for all involved when more then one person is receiving help in a thread.

Thanks

---

### Post by Yellow Pasque on 2020-05-12
Any clues in dmesg or 'sudo journalctl -b'?

---

### Post by collin80 on 2020-05-17
> **enon97 said:**
> [COLOR=#212529][FONT=Inconsolata]
[/FONT][/COLOR]This is the only line I get: 
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 630 (rev 04)

Just in case, my laptop model is this: [https://es.msi.com/Laptop/GL72VR-7RFX](https://es.msi.com/Laptop/GL72VR-7RFX)

Any help would be appreciated.


Try reinstalling the nvidia drivers. This caused it to enumerate the nvidia card for me but then something else was broken that caused the GUI to not come up and I had to use the command line. But, I wonder if you will not have that problem.

---

