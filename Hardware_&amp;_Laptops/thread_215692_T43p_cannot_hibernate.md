---
title: "T43p cannot hibernate"
date: 2006-07-14
forum: Hardware &amp; Laptops
---

### Post by iCeZuLy on 2006-07-14
I just installed Dapper and Compiz xgl on my laptop Thinkpad T43p.Most functions are out of box. But I cannot use hibernation after I installed fglrx & compiz xgl. Would you please help me find out this problem? 

Thank you very much!

---

### Post by iCeZuLy on 2006-07-14
I copied the related &#65295;ar/log/message as following:
> Jul 14 16:56:46 localhost kernel: [17184100.096000] ACPI: PCI interrupt for device 0000:0b:02.0 disabled
Jul 14 16:56:46 localhost kernel: [17184100.100000] ath_pci: driver unloaded
Jul 14 16:56:46 localhost kernel: [17184100.100000] ath_rate_sample: unloaded
Jul 14 16:56:46 localhost kernel: [17184100.104000] ath_hal: driver unloaded
Jul 14 16:56:46 localhost kernel: [17184100.152000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
Jul 14 16:57:10 localhost kernel: [17184106.272000] Freezing cpus ...
Jul 14 16:57:11 localhost kernel: [17184106.272000] Stopping tasks: ========================================================================================================|
Jul 14 16:57:11 localhost kernel: [17184106.276000] Shrinking memory...  ^H-^H\^H|^H/^H-^H\^H|^Hdone (86300 pages freed)
Jul 14 16:57:11 localhost kernel: [17184109.908000] ACPI: PCI interrupt for device 0000:0b:00.0 disabled
Jul 14 16:57:11 localhost kernel: [17184116.892000] ACPI: PCI interrupt for device 0000:01:00.0 disabled
Jul 14 16:57:11 localhost kernel: [17184116.908000] ACPI: PCI interrupt for device 0000:00:1e.2 disabled
Jul 14 16:57:11 localhost kernel: [17184116.908000] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
Jul 14 16:57:11 localhost kernel: [17184116.940000] ACPI: PCI interrupt for device 0000:00:1d.3 disabled
Jul 14 16:57:11 localhost kernel: [17184116.940000] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
Jul 14 16:57:11 localhost kernel: [17184116.940000] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
Jul 14 16:57:11 localhost kernel: [17184116.940000] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
Jul 14 16:57:11 localhost kernel: [17184116.940000] ................................swsusp: Need to copy 126596 pages
Jul 14 16:57:11 localhost kernel: [17184116.940000] swsusp: Restoring Highmem
Jul 14 16:57:11 localhost kernel: [17184118.940000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
Jul 14 16:57:11 localhost kernel: [17184118.940000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 20 (level, low) -> IRQ 177
Jul 14 16:57:11 localhost kernel: [17184118.940000] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 22 (level, low) -> IRQ 185
Jul 14 16:57:11 localhost kernel: [17184118.940000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 169
Jul 14 16:57:11 localhost kernel: [17184118.940000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 233
Jul 14 16:57:11 localhost kernel: [17184118.940000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 50
Jul 14 16:57:11 localhost kernel: [17184118.940000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 58
Jul 14 16:57:11 localhost kernel: [17184118.956000] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
Jul 14 16:57:11 localhost kernel: [17184118.956000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 19 (level, low) -> IRQ 58
Jul 14 16:57:11 localhost kernel: [17184118.956000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 22 (level, low) -> IRQ 185
Jul 14 16:57:11 localhost kernel: [17184119.224000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 169
Jul 14 16:57:11 localhost kernel: [17184119.300000] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 169
Jul 14 16:57:11 localhost kernel: [17184120.064000] ata1: dev 0 configured for UDMA/100
Jul 14 16:57:11 localhost kernel: [17184120.548000] ata2: dev 0 configured for UDMA/33
Jul 14 16:57:11 localhost kernel: [17184123.576000] Restarting tasks... done
Jul 14 16:57:11 localhost kernel: [17184123.584000] Thawing cpus ...
Jul 14 16:57:14 localhost kernel: [17184128.380000] ndiswrapper version 1.8 loaded (preempt=yes,smp=yes)
Jul 14 16:57:14 localhost kernel: [17184128.556000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
Jul 14 16:57:14 localhost kernel: [17184128.716000] ath_rate_sample: 1.2
Jul 14 16:57:14 localhost kernel: [17184128.784000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
Jul 14 16:57:14 localhost kernel: [17184128.784000] ACPI: PCI Interrupt 0000:0b:02.0[A] -> GSI 21 (level, low) -> IRQ 66
Jul 14 16:57:15 localhost kernel: [17184129.004000] Build date: Jul 10 2006
Jul 14 16:57:15 localhost kernel: [17184129.004000] Debugging version (IEEE80211)
Jul 14 16:57:15 localhost kernel: [17184129.004000] ath0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Jul 14 16:57:15 localhost kernel: [17184129.004000] ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
Jul 14 16:57:15 localhost kernel: [17184129.004000] ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Jul 14 16:57:15 localhost kernel: [17184129.004000] ath0: H/W encryption support: WEP AES AES_CCM TKIP
Jul 14 16:57:15 localhost kernel: [17184129.004000] ath0: mac 5.9 phy 4.3 radio 3.6
Jul 14 16:57:15 localhost kernel: [17184129.004000] ath0: Use hw queue 1 for WME_AC_BE traffic
Jul 14 16:57:15 localhost kernel: [17184129.008000] ath0: Use hw queue 0 for WME_AC_BK traffic
Jul 14 16:57:15 localhost kernel: [17184129.008000] ath0: Use hw queue 2 for WME_AC_VI traffic
Jul 14 16:57:15 localhost kernel: [17184129.008000] ath0: Use hw queue 3 for WME_AC_VO traffic
Jul 14 16:57:15 localhost kernel: [17184129.008000] ath0: Use hw queue 8 for CAB traffic
Jul 14 16:57:15 localhost kernel: [17184129.008000] ath0: Use hw queue 9 for beacons
Jul 14 16:57:15 localhost kernel: [17184129.008000] Debugging version (ATH)
Jul 14 16:57:15 localhost kernel: [17184129.008000] ath0: Atheros 5212: mem=0xb4000000, irq=66
Jul 14 16:57:15 localhost kernel: [17184129.312000] tg3.c:v3.47 (Dec 28, 2005)
Jul 14 16:57:15 localhost kernel: [17184129.312000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 169
Jul 14 16:57:15 localhost kernel: [17184129.352000] eth0: Tigon3 [partno(BCM95751M) rev 4101 PHY(5750)] (PCI Express) 10/100/1000BaseT Ethernet 00:01:6c:e9:38:03
Jul 14 16:57:15 localhost kernel: [17184129.352000] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[1] TSOcap[1] 
Jul 14 16:57:15 localhost kernel: [17184129.352000] eth0: dma_rwctrl[76180000]
Jul 14 16:57:20 localhost kernel: [17184132.484000] ACPI: Power Button (FF) [PWRF]
Jul 14 16:57:20 localhost kernel: [17184132.484000] ACPI: Lid Switch [LID]
Jul 14 16:57:20 localhost kernel: [17184132.484000] ACPI: Sleep Button (CM) [SLPB]
Jul 14 16:57:21 localhost kernel: [17184132.988000] ACPI: Thermal Zone [THM0] (52 C)
Jul 14 16:57:21 localhost kernel: [17184133.268000] ibm_acpi: IBM ThinkPad ACPI Extras v0.12a
Jul 14 16:57:21 localhost kernel: [17184133.268000] ibm_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
Jul 14 16:57:21 localhost kernel: [17184133.700000] ACPI: AC Adapter [AC] (on-line)
Jul 14 16:57:21 localhost kernel: [17184133.764000] ACPI: Battery Slot [BAT0] (battery absent)

---

