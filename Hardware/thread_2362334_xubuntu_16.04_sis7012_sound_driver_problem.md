---
title: "xubuntu 16.04 sis7012 sound driver problem"
date: 2017-05-27
forum: Hardware
---

### Post by aliasvector on 2017-05-27
Hello.
I have just installed the xubuntu 16.04 LTS Xenial Xerus on my old laptop. It has SIS650 integrated graphics which driver I have found, build and setup sucessfully.
Also my laptop has SIS7012 AC'97 audio chip:
```

user@Rover:/etc$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS961 [MuTIOL Media IO]
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2/3 SMBus controller
00:02.2 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.3 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 IDE Controller (rev d0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS7012 AC'97 Sound Controller (rev a0)
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter (rev 10)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter

```

I have found the sources of the old sis driver for kernel 2.4.x, but I cannot compile it for 4.8.x of xubuntu.
After some googling I found that the sis7012 seems should be supported by snd_intel8x0.
I have tried 
modprobe snd_inter8x0
but nothing is changed.
I have still have not sound enabled on my laptop. 
Alsamixer als cannot be started. It produces the error "Cannot open mixer: no such file or catalog".
So, does anybody know how to enable sound in this xubuntu version for sis7012?

---

### Post by aliasvector on 2017-05-30
I have found a strange error in dmesg output:
```

snd_intel8x0 0000:00:02.7: can't find IRQ for PCI INT C
genirq: Flags mismatch irq 0. 00000080 (snd_intel8x0) vs. 00015a00 (timer)
snd_intel8x0 0000:00:02.7: unable to grab IRQ 0

```

I have tried to provide the kernel parameter pci=biosirq in grub configuration, but this didn't help. Seems the driver is found correctly, but it cannot to be loaded due to some kernel-bios inconsitency.
Does anyone know how to solve this error?

---

