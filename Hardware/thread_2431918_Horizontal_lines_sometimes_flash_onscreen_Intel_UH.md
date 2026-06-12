---
title: "Horizontal lines sometimes flash onscreen Intel UHD 620"
date: 2019-11-24
forum: Hardware
---

### Post by greedylizard on 2019-11-24
Hello, I have had this issue intermittently for a while, but held off on asking about it because I was trying to figure out what triggers it to no success. Periodically, horizontal, usually white, lines flash on the screen and disappear just as quickly. I cannot figure out what in the world triggers it, but it seems more likely to start happening when I have been using my computer for a while. Interestingly, it does not seem to occur on a second monitor when I connect my laptop to it via an HDMI cable. I had a previous display issue I posted about here that was resolved, but might be related: [https://ubuntuforums.org/showthread.php?t=2429810](https://ubuntuforums.org/showthread.php?t=2429810) Even back before I resolved this previous issue, the horizontal lines flashing onscreen occurred. In addition, the problem existed on both 19.04 and 19.10 when I upgraded.

Here are the results for
```
lspci
```
Output:
```
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers (rev 08)
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 620 (rev 07)
00:08.0 System peripheral: Intel Corporation Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th Gen Core Processor Gaussian Mixture Model
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:15.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #0 (rev 21)
00:15.1 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #1 (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI #1 (rev 21)
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #6 (rev f1)
00:1d.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #9 (rev f1)
00:1e.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO UART Controller #0 (rev 21)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point LPC Controller/eSPI Controller (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
01:00.0 Network controller: Intel Corporation Wireless 8265 / 8275 (rev 78)
02:00.0 Non-Volatile memory controller: Phison Electronics Corporation E12 NVMe Controller (rev 01)
```

I'm willing to try various suggestions out to resolve this, but keep in mind I will have to try each suggestion out for a while to make sure the issue is resolved since the problem is intermittent.

---

### Post by greedylizard on 2019-12-18
So I have made a bizarre discovery about these artefacts. If I go into my BIOS settings and change the Power Profile from Balanced to Performance the issue stops. However, if I ever close my laptop lid after that, even if I have set in Gnome Tweaks for the laptop not to suspend when the lid is closed, the artefacts start appearing again after the lid is reopened. After that the issue will persist across reboots until I go into the BIOS settings and change the Power Profile back to Balanced then go into the BIOS again to set it to Performance. I am completely baffled, but I hope these extra details means someone has a suggestion!

---

### Post by greedylizard on 2019-12-18
It seems that having the screen turn off because it was idle for too long also causes the artefacts upon waking the screen.

---

### Post by greedylizard on 2019-12-30
Ended up sending the laptop to the manufacturer, it was a hardware issue and is now fixed.

---

### Post by shans10 on 2019-12-30
What is your laptop model? I have the same problem on my HP ProBook 440 G5 and I always thought it was a software problem since I do not face this problem in bios or any text based environment. How long have you tested your laptop after repair?

---

### Post by shans10 on 2020-03-27
> **greedylizard said:**
> Ended up sending the laptop to the manufacturer, it was a hardware issue and is now fixed.

Can you share what the hardware issue was?

---

