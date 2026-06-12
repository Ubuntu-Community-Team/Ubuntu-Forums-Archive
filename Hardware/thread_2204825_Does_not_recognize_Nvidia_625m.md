---
title: "Does not recognize Nvidia 625m"
date: 2014-02-10
forum: Hardware
---

### Post by vinicius3 on 2014-02-10
Hi!
I have a Dell Inpiron i14 2640 with Nvidia 625m and Intel Graphics HD but Mint just recognize intel card.
I'm using Mint 16 KDE
the command "lspci | grep VGA" only returns:
```
CODE: SELECT ALL
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)

```

and inxi -Fxz:


```
.....
Graphics:  Card: Intel 3rd Gen Core processor Graphics Controller bus-ID: 00:02.0 
           X.Org: 1.14.5 drivers: intel (unloaded: fbdev,vesa) Resolution: 1366x768@60.0hz 
           GLX Renderer: N/A GLX Version: N/A Direct Rendering: N/A
....

```

I tried installing bumblebee, but it did not work.


What can I do?

---

### Post by Yellow Pasque on 2014-02-11
the nvidia card is usually listed as a 3D controller. Show full output of lspci:
```
sudo update-pciids
lspci -k
```

---

### Post by vinicius3 on 2014-02-11
Hi!
the command "lspci-k" returned:

```
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)                                                         Subsystem: Dell Device 0591                                                                                                    
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)                            
        Kernel driver in use: pcieport                                                                                                 
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)                               
        Subsystem: Dell Device 0591                                                                                                    
        Kernel driver in use: i915                                                                                                     
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)                        
        Subsystem: Dell Device 0591                                                                                                    
        Kernel driver in use: xhci_hcd                                                                                                 
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)                     
        Subsystem: Dell Device 0591
        Kernel driver in use: mei_me
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
        Subsystem: Dell Device 0591
        Kernel driver in use: ehci-pci
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
        Subsystem: Dell Device 0591
        Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
        Kernel driver in use: pcieport
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
        Kernel driver in use: pcieport
00:1c.5 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 6 (rev c4)
        Kernel driver in use: pcieport
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
        Subsystem: Dell Device 0591
        Kernel driver in use: ehci-pci
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
        Subsystem: Dell Device 0591
        Kernel driver in use: lpc_ich
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
        Subsystem: Dell Device 0591
        Kernel driver in use: ahci
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
        Subsystem: Dell Device 0591
02:00.0 3D controller: NVIDIA Corporation GF117M [GeForce 610M/710M/820M / GT 620M/625M/630M/720M] (rev ff)
06:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
        Subsystem: Dell Device 0209
        Kernel driver in use: ath9k
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
        Subsystem: Dell Device 0591
        Kernel driver in use: r8169



```


but how can I use the nvidia video and set it on nvidia-settings?

---

### Post by Yellow Pasque on 2014-02-11
> I tried installing bumblebee, but it did not work.
Be more specific. What happened? Logs?

---

### Post by vinicius3 on 2014-02-11
```
 [1]:~ > optirun google-chrome
[  405.537627] [ERROR]Cannot access secondary GPU - error: Could not load GPU driver


[  405.537754] [ERROR]Aborting because fallback start is disabled.
```

And:

[IMG]https://lh6.googleusercontent.com/VQOaN-sRpsdrxSPHVwnhbo9JYg0Sic5sEeEo6hZfHvg=w931-h592-no[/IMG]

---

