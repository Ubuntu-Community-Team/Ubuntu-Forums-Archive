---
title: "Brutal shutdowns on Olidata Stainer 3050"
date: 2008-01-23
forum: Hardware &amp; Laptops
---

### Post by quadrispro on 2008-01-23
Hi, I have an [Olidata Stainer 3050]("http://www.olidata.com/Prodotti_vendita/Prodotti/Configurazioni/Scheda_conf.asp?conf=SpecTecPerfext_Stainer3050") and some problem with Ubuntu 7.10 (for i386).

At the moment, the most important is represented by random brutal shutdowns: at the first lock-up of touchpad and kboard, then the system shutdowns. 

This is the message that temperature applet gives me few seconds before the system shutdowns:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=57295&stc=1&d=1201090862[/IMG]

And this is my syslog:

```

Jan 23 12:10:54 quadrispro-laptop kernel: [13178.228000] APIC error on CPU0: 40(40)
Jan 23 12:10:54 quadrispro-laptop kernel: [13178.228000] APIC error on CPU1: 40(40)
Jan 23 12:15:55 quadrispro-laptop kernel: [13479.760000] ACPI: EC: acpi_ec_wait timeout, status = 10, expect_event = 2
Jan 23 12:15:55 quadrispro-laptop kernel: [13479.760000] ACPI: EC: write_cmd timeout, command = 128
Jan 23 12:15:55 quadrispro-laptop kernel: [13479.760000] ACPI Exception (evregion-0420): AE_TIME, Returned by Handler for [EmbeddedControl] [20070126]
Jan 23 12:15:55 quadrispro-laptop kernel: [13479.760000] ACPI Exception (dswexec-0462): AE_TIME, While resolving operands for [OpcodeName unavailable] [20070126]
Jan 23 12:15:55 quadrispro-laptop kernel: [13479.760000] ACPI Error (psparse-0551): Method parse/execution failed [\_TZ_.TZ00._TMP] (Node df8137c8), AE_TIME
Jan 23 12:16:47 quadrispro-laptop syslogd 1.4.1#21ubuntu3: restart.

```

lspci:
```

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)

```

---

