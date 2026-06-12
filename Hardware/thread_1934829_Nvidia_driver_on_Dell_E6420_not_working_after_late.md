---
title: "Nvidia driver on Dell E6420 not working after latest updates"
date: 2012-03-02
forum: Hardware
---

### Post by damend on 2012-03-02
After the updates just released are applied, my nvidia card is no longer detected (Additional Drivers shows no drivers). Previously it was working fine but after running the latest updates the other day, I saw really slow performance watching video.

Also, when I startx from console, I get the error "(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)."

Anyone else getting this issue?


Running 11.10 with all latest updates.

---

### Post by rajgautam on 2012-03-11
From what I have found, it has two graphics chips - one in the CPU itself and other one nvidia card in PCIe bus.

$ lspci  | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: nVidia Corporation GF108 [Quadro NVS 4200M] (rev a1)
$

The laptop display is connected to Intel graphics (HD 3000) and HDMI port is connected to Nvidia chip(BUSID "PCI:01:00:00").

Can you post your xorg.conf?
You might want to try running nvidia-xconfig..

---

### Post by paulphillips on 2012-06-05
Hi - this may not help you, but I found no nvidia support when I installed 12.04

After lots of searching, found that the BIOS setting for "Optimus" Nvidia technology was enabled when it should not have been.  Apparently it's only for Windows.

Disabled it, and nvidia now detects fine!

---

