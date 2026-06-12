---
title: "Graphics card not being detected"
date: 2008-10-21
forum: General Help
---

### Post by keely on 2008-10-21
My graphics card isn't being detected when i turn on my computer.
Does anyone know a solution?

---

### Post by Kevbert on 2008-10-21
Welcome to Ubuntu.
Please enter the following command in Applications-Accessories-Terminal
```
lspci
```
Copy the output by highlighting it with the mouse and then press Ctrl-Shift-C. Paste it in a new post with Ctrl-V.
You could try selecting System-Administration-Software Sources and make sure just the top four boxes under the Ubuntu Software tab are ticked and Important, Recommended and Unsupported boxes under the Updates Tab are ticked. Then hopefully it will tell you your sources are out of date and ask you to reload them.  At this point the Display adapter should be recognised.

---

### Post by keely on 2008-10-21
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

---

### Post by 3rdalbum on 2008-10-21
What happens if you go to System > Administration > Hardware Drivers? Does it show you an Nvidia driver that you can enable?

---

### Post by Kevbert on 2008-10-21
> **3rdalbum said:**
> What happens if you go to System > Administration > Hardware Drivers? Does it show you an Nvidia driver that you can enable?

Yup, that should work.
It may even be worth regenerating the xorg.conf file which resides in the /etc/X11 directory in terminal with
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
if 3rdalbum's suggestion fails.
The driver in the xorg.file should be 'nvidia'.  I've attached my xorg file and that is what should be eventually generated using the above command (less the .txt at the end).

---

### Post by keely on 2008-10-22
Thanks everyone, I updated all my computer software,
then enabled the nvidia driver and everything seems to be working
perfectly.

---

