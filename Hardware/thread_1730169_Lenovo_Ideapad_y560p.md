---
title: "Lenovo Ideapad y560p"
date: 2011-04-15
forum: Hardware
---

### Post by fallenangel3787 on 2011-04-15
Having troubles with my laptop audio, im kind of new to ubuntu (have used it on my old laptop but still learning) and it seems my built-in mic doesnt work. my built in webcam works fine but i dont have any inputs at all in my sound control. nothing is picked up as if there isnt a mic at all.

Dont know if this will help at all 


> 00:00.0 Host bridge: Intel Corporation Sandy Bridge DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Sandy Bridge PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 4 (rev b5)
00:1c.6 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 7 (rev b5)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Cougar Point LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Madison [Mobility Radeon HD 5000 Series]
01:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
03:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
09:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 20)
09:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 20)
09:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 20)
09:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 20)I have looked everywhere and cant find anything that works.

---

### Post by stirfoo on 2011-04-26
One thing I noticed. Every now and then I have to re-select the device for sound input. It's in the Sound Preferences menu, Input tab, when you click on the speaker icon.

* Internal Analog Audio Stereo

This is the only device listed on my box but sometimes it just needs to be clicked. Then the Input Level meter above will bounce when I speak, and I can record.

We have the same chip set so you should see the same device.

---

### Post by fallenangel3787 on 2011-04-26
Under the input tab there are no options to be select. its as if there is no input device/its not detecting an input device.

---

### Post by infomissing123 on 2011-05-10
Try alsamixer (cmd line) and make sure that the line in and microphone volumes are all the way up.  I have this laptop and they are disabled by default for some reason.

---

### Post by meitham on 2011-06-07
> **fallenangel3787 said:**
> Having troubles with my laptop audio, im kind of new to ubuntu (have used it on my old laptop but still learning) and it seems my built-in mic doesnt work. my built in webcam works fine but i dont have any inputs at all in my sound control. nothing is picked up as if there isnt a mic at all.

Dont know if this will help at all 


I have looked everywhere and cant find anything that works.
Have you actually found a fix for your audio issue?

---

