---
title: "installing drivers for AOC moniter"
date: 2015-01-13
forum: Hardware
---

### Post by ben131 on 2015-01-13
Hello

I am trying to get my moniter working with Ubuntu and have had trouble making that happen. I am using (or trying to use) the AOC e2243fwk moniter as a second monitor. The only drivers that I have found on their website are a zip file with a '.cat', '.icm', and a '.icm' file in it. My question is how do I install drivers using a zip file like this, or how can I get my moniter working in another way.

Edit:
I forgot to mention that I contacted their customer support and all they said that they only support windows and macs via customer support BUT... they are emailing an engineer

---

### Post by buzzingrobot on 2015-01-13
Can't help with the multiple monitor issue, but the .icm files are likely a default color profile for the monitor provided by AOC.  You can install it via System Settings->Color. 

To extract files from the archive, right click on it in Nautilus, the file manager, and select "Extract Here".

Before someone else comes along to ask, you should let us know your hardware specs, including the video card.  That'll help work the monitors issue.

---

### Post by ben131 on 2015-01-13
How do I properly give the right information for my hardware specs/video card?

---

### Post by buzzingrobot on 2015-01-13
One way is to open a Terminal (ctrl-alt-t will pop one up) and execute this command: lspci.  Then, grab the text it generates with the mouse and paste it into a post here. Select it again and click on the dialogue balloon icon in the row above the entry field to wrap quotes around it.

---

### Post by ben131 on 2015-01-13
> 00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 0b)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)
00:14.0 USB controller: Intel Corporation Lynx Point-LP USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation Lynx Point-LP HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation Lynx Point-LP HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 1 (rev e4)
00:1c.2 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 3 (rev e4)
00:1c.3 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 4 (rev e4)
00:1c.4 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 5 (rev e4)
00:1d.0 USB controller: Intel Corporation Lynx Point-LP USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Lynx Point-LP LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Lynx Point-LP SMBus Controller (rev 04)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
02:00.0 Network controller: Intel Corporation Wireless 7260 (rev 73)
09:00.0 3D controller: NVIDIA Corporation GK208M [GeForce GT 730M] (rev a1)



Ok, here it is

---

