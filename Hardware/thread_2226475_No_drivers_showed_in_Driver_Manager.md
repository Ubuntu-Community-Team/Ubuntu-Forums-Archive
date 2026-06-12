---
title: "No drivers showed in Driver Manager"
date: 2014-05-27
forum: Hardware
---

### Post by Ubi_one_2014 on 2014-05-27
Hi

Using Ubuntu 14.04 LTS version on a 64bits dell laptop

```
kubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)                                                                                                                                           
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)                                                                                                                         
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)                                                                                                                  
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)                                                                                                               
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)                                                                                                           
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)                                                                                                            
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)                                                                                                                       
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)                                                                                                                       
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)                                                                                                           
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)                                                                                                                                               
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)                                                                                                                   
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)                                                                                                                                   
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
02:00.0 Network controller: Intel Corporation Centrino Wireless-N 2230 (rev c4)


```

when opening driver manager, no driver seems to be available
i seems to be running a intel graphics controller

how do i obtain a driver for this card?

Thanks

---

### Post by Yellow Pasque on 2014-05-27
The intel graphics drivers are open-source and installed by default. You already have them.

---

### Post by LastDino on 2014-05-27
No need to try that, like Temujin has pointed out, Ubuntu installs them by default as they are open sourced.

---

### Post by matt_symes on 2014-05-27
Hi

Try ```
lspci -k
```

Kind regards

---

