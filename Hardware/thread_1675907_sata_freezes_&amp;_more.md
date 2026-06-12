---
title: "sata freezes &amp; more"
date: 2011-01-26
forum: Hardware
---

### Post by Florian Reinhard on 2011-01-26
my laptop just got sticky and unresponsive. it's a fujitsu siemens lifebook s7010. all i found related to the things listed below are to use another sata cable, which is somehow impossible for laptops.

dmesg showed this:

```

[63041.000086] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[63041.000100] ata3.00: failed command: READ DMA
[63041.000117] ata3.00: cmd c8/00:08:28:f9:1a/00:00:00:00:00/e0 tag 0 dma 4096 in
[63041.000120]          res 40/00:fe:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
[63041.000128] ata3.00: status: { DRDY }
[63041.000141] ata3: hard resetting link
[63041.992064] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[63041.993306] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[63041.993317] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[63041.996359] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[63041.996370] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[63041.996586] ata3.00: configured for UDMA/100
[63041.996596] ata3.00: device reported invalid CHS sector 0
[63041.996613] ata3: EH complete
[63073.000078] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[63073.000092] ata3.00: failed command: READ DMA
[63073.000108] ata3.00: cmd c8/00:08:38:f9:1a/00:00:00:00:00/e0 tag 0 dma 4096 in
[63073.000112]          res 40/00:fe:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
[63073.000120] ata3.00: status: { DRDY }
[63073.000132] ata3: hard resetting link
[63073.992066] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[63073.993300] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[63073.993311] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[63073.996360] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[63073.996371] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[63073.996585] ata3.00: configured for UDMA/100
[63073.996595] ata3.00: device reported invalid CHS sector 0
[63073.996613] ata3: EH complete
[63105.000084] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[63105.000097] ata3.00: failed command: READ DMA
[63105.000114] ata3.00: cmd c8/00:08:40:f9:1a/00:00:00:00:00/e0 tag 0 dma 4096 in
[63105.000118]          res 40/00:fe:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
[63105.000126] ata3.00: status: { DRDY }
[63105.000138] ata3: hard resetting link
[63105.992051] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[63105.993102] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[63105.993107] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[63105.995902] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[63105.995907] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[63105.996218] ata3.00: configured for UDMA/100
[63105.996229] ata3.00: device reported invalid CHS sector 0
[63105.996246] ata3: EH complete
[63138.000068] ata3: limiting SATA link speed to 1.5 Gbps
[63138.000080] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[63138.000092] ata3.00: failed command: READ DMA
[63138.000108] ata3.00: cmd c8/00:08:50:f9:1a/00:00:00:00:00/e0 tag 0 dma 4096 in
[63138.000112]          res 40/00:fe:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
[63138.000120] ata3.00: status: { DRDY }
[63138.000132] ata3: hard resetting link
[63138.992066] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[63138.993305] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[63138.993316] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[63138.996361] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[63138.996372] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[63138.996593] ata3.00: configured for UDMA/100
[63138.996604] ata3.00: device reported invalid CHS sector 0
[63138.996622] ata3: EH complete
[63170.000070] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[63170.000083] ata3.00: failed command: READ DMA
[63170.000099] ata3.00: cmd c8/00:08:68:f9:1a/00:00:00:00:00/e0 tag 0 dma 4096 in
[63170.000103]          res 40/00:fe:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
[63170.000111] ata3.00: status: { DRDY }
[63170.000124] ata3: hard resetting link
[63170.992069] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[63170.993300] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[63170.993311] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[63170.996360] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[63170.996370] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[63170.996583] ata3.00: configured for UDMA/100
[63170.996594] ata3.00: device reported invalid CHS sector 0
[63170.996611] ata3: EH complete
[63202.000077] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[63202.000090] ata3.00: failed command: READ DMA
[63202.000106] ata3.00: cmd c8/00:08:70:f9:1a/00:00:00:00:00/e0 tag 0 dma 4096 in
[63202.000110]          res 40/00:fe:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
[63202.000118] ata3.00: status: { DRDY }
[63202.000130] ata3: hard resetting link
[63202.992069] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[63202.993306] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[63202.993317] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[63202.996366] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[63202.996377] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[63202.996589] ata3.00: configured for UDMA/100
[63202.996599] ata3.00: device reported invalid CHS sector 0
[63202.996616] ata3: EH complete
[63234.000074] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[63234.000087] ata3.00: failed command: READ DMA
[63234.000104] ata3.00: cmd c8/00:08:78:f9:1a/00:00:00:00:00/e0 tag 0 dma 4096 in
[63234.000107]          res 40/00:fe:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
[63234.000115] ata3.00: status: { DRDY }
[63234.000127] ata3: hard resetting link
[63234.992063] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[63234.993291] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[63234.993302] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[63234.996377] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[63234.996389] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[63234.996612] ata3.00: configured for UDMA/100
[63234.996623] ata3.00: device reported invalid CHS sector 0
[63234.996639] ata3: EH complete
[63266.000061] ata3.00: limiting speed to UDMA/66:PIO4
[63266.000073] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[63266.000085] ata3.00: failed command: READ DMA
[63266.000101] ata3.00: cmd c8/00:08:18:f9:1a/00:00:00:00:00/e0 tag 0 dma 4096 in
[63266.000105]          res 40/00:fe:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
[63266.000113] ata3.00: status: { DRDY }
[63266.000125] ata3: hard resetting link
[63266.992066] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[63266.993313] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[63266.993324] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[63266.996366] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[63266.996377] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[63266.996589] ata3.00: configured for UDMA/66
[63266.996600] ata3.00: device reported invalid CHS sector 0
[63266.996617] ata3: EH complete
[63299.000081] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[63299.000094] ata3.00: failed command: READ DMA
[63299.000110] ata3.00: cmd c8/00:08:88:f9:1a/00:00:00:00:00/e0 tag 0 dma 4096 in
[63299.000114]          res 40/00:fe:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
[63299.000122] ata3.00: status: { DRDY }
[63299.000135] ata3: hard resetting link
[63299.992072] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[63299.993297] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[63299.993308] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[63299.996341] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[63299.996352] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[63299.996555] ata3.00: configured for UDMA/66
[63299.996566] ata3.00: device reported invalid CHS sector 0
[63299.996582] ata3: EH complete
[63331.000084] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[63331.000098] ata3.00: failed command: READ DMA
[63331.000114] ata3.00: cmd c8/00:08:90:f9:1a/00:00:00:00:00/e0 tag 0 dma 4096 in
[63331.000118]          res 40/00:fe:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
[63331.000126] ata3.00: status: { DRDY }
[63331.000138] ata3: hard resetting link
[63331.992075] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[63331.993314] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[63331.993325] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[63331.996364] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[63331.996375] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[63331.996585] ata3.00: configured for UDMA/66
[63331.996596] ata3.00: device reported invalid CHS sector 0
[63331.996613] ata3: EH complete
[63363.000079] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[63363.000093] ata3.00: failed command: READ DMA
[63363.000109] ata3.00: cmd c8/00:08:98:f9:1a/00:00:00:00:00/e0 tag 0 dma 4096 in
[63363.000113]          res 40/00:fe:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
[63363.000121] ata3.00: status: { DRDY }
[63363.000134] ata3: hard resetting link
[63363.992069] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[63363.993293] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[63363.993304] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[63363.996342] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[63363.996352] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[63363.996558] ata3.00: configured for UDMA/66
[63363.996568] ata3.00: device reported invalid CHS sector 0
[63363.996584] ata3: EH complete
[63396.000086] ata3.00: limiting speed to UDMA/33:PIO4
[63396.000098] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[63396.000110] ata3.00: failed command: READ DMA
[63396.000126] ata3.00: cmd c8/00:08:a0:f9:1a/00:00:00:00:00/e0 tag 0 dma 4096 in
[63396.000130]          res 40/00:fe:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
[63396.000138] ata3.00: status: { DRDY }
[63396.000151] ata3: hard resetting link
[63396.992064] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[63396.993296] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[63396.993307] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[63396.996342] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[63396.996353] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[63396.996562] ata3.00: configured for UDMA/33
[63396.996572] ata3.00: device reported invalid CHS sector 0
[63396.996587] ata3: EH complete
[63431.000085] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[63431.000098] ata3.00: failed command: READ DMA
[63431.000115] ata3.00: cmd c8/00:08:00:59:04/00:00:00:00:00/e5 tag 0 dma 4096 in
[63431.000119]          res 40/00:fe:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
[63431.000127] ata3.00: status: { DRDY }
[63431.000139] ata3: hard resetting link
[63431.992065] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[63431.993300] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[63431.993312] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[63431.996357] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[63431.996368] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[63431.996570] ata3.00: configured for UDMA/33
[63431.996579] ata3.00: device reported invalid CHS sector 0
[63431.996596] ata3: EH complete
[63465.000078] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[63465.000092] ata3.00: failed command: READ DMA
[63465.000108] ata3.00: cmd c8/00:08:08:59:04/00:00:00:00:00/e5 tag 0 dma 4096 in
[63465.000112]          res 40/00:fe:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
[63465.000120] ata3.00: status: { DRDY }
[63465.000133] ata3: hard resetting link
[63465.992063] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[63465.993294] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[63465.993305] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[63465.996341] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[63465.996351] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[63465.996558] ata3.00: configured for UDMA/33
[63465.996569] ata3.00: device reported invalid CHS sector 0
[63465.996585] ata3: EH complete
[63498.000086] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[63498.000099] ata3.00: failed command: READ DMA
[63498.000115] ata3.00: cmd c8/00:08:08:08:44/00:00:00:00:00/e5 tag 0 dma 4096 in
[63498.000119]          res 40/00:fe:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
[63498.000127] ata3.00: status: { DRDY }
[63498.000139] ata3: hard resetting link
[63498.992063] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[63498.993299] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[63498.993310] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[63498.996370] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[63498.996381] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[63498.997207] ata3.00: configured for UDMA/33
[63498.997218] ata3.00: device reported invalid CHS sector 0
[63498.997234] ata3: EH complete
[63530.000080] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[63530.000094] ata3.00: failed command: READ DMA
[63530.000110] ata3.00: cmd c8/00:08:70:09:44/00:00:00:00:00/e5 tag 0 dma 4096 in
[63530.000114]          res 40/00:fe:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
[63530.000122] ata3.00: status: { DRDY }
[63530.000135] ata3: hard resetting link
[63530.992062] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[63530.993293] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[63530.993304] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[63530.996344] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[63530.996355] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[63530.996563] ata3.00: configured for UDMA/33
[63530.996574] ata3.00: device reported invalid CHS sector 0
[63530.996589] ata3: EH complete
[63562.000085] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[63562.000099] ata3.00: failed command: READ DMA
[63562.000115] ata3.00: cmd c8/00:08:78:c0:ce/00:00:00:00:00/e5 tag 0 dma 4096 in
[63562.000119]          res 40/00:fe:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
[63562.000127] ata3.00: status: { DRDY }
[63562.000139] ata3: hard resetting link
[63562.992064] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[63562.993308] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[63562.993319] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[63562.996350] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[63562.996361] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[63562.996553] ata3.00: configured for UDMA/33
[63562.996564] ata3.00: device reported invalid CHS sector 0
[63562.996579] ata3: EH complete


```

---

