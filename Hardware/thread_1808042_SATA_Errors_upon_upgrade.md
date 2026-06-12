---
title: "SATA Errors upon upgrade"
date: 2011-07-19
forum: Hardware
---

### Post by Nycthbris on 2011-07-19
I just upgraded to 10.10 from 10.04 (yeah outdated, I know) and came across these errors. They show up in dmesg after I hear a click followed by a spin-down sound from my HD. I know this is usually the sound of the drive dying, but I have reason to believe otherwise because if I reinstall 10.04, the problem does not occur.

I've had similar errors using other distros with kernels more recent than 2.6.32. This makes me think it's a SATA driver error.

Thoughts?

Output from dmesg:
```
[  826.510902] ata5: exception Emask 0x10 SAct 0x0 SErr 0x4090000 action 0xe frozen
[  826.510908] ata5: irq_stat 0x00400040, connection status changed
[  826.510913] ata5: SError: { PHYRdyChg 10B8B DevExch }
[  826.510921] ata5: hard resetting link
[  826.511488] ata4: exception Emask 0x10 SAct 0x0 SErr 0x4090000 action 0xe frozen
[  826.511492] ata4: irq_stat 0x00400040, connection status changed
[  826.511496] ata4: SError: { PHYRdyChg 10B8B DevExch }
[  826.511502] ata4: hard resetting link
[  826.511514] ata6: exception Emask 0x50 SAct 0x0 SErr 0x4090800 action 0xe frozen
[  826.511518] ata6: irq_stat 0x00400040, connection status changed
[  826.511522] ata6: SError: { HostInt PHYRdyChg 10B8B DevExch }
[  826.511527] ata6: hard resetting link
[  831.540145] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  831.551195] ata5.00: configured for UDMA/133
[  831.551198] ata5: EH complete
[  831.916103] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  831.925198] ata6.00: configured for UDMA/133
[  831.925203] ata6: EH complete
[  832.205555] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  832.236680] ata4.00: configured for UDMA/133
[  832.236687] ata4: EH complete
[ 1069.119943] ata4: exception Emask 0x10 SAct 0x0 SErr 0x4090000 action 0xe frozen
[ 1069.119949] ata4: irq_stat 0x00400040, connection status changed
[ 1069.119967] ata4: SError: { PHYRdyChg 10B8B DevExch }
[ 1069.119971] ata4: hard resetting link
[ 1069.119973] ata5: exception Emask 0x10 SAct 0x0 SErr 0x4090000 action 0xe frozen
[ 1069.119975] ata5: irq_stat 0x00400040, connection status changed
[ 1069.119977] ata5: SError: { PHYRdyChg 10B8B DevExch }
[ 1069.119979] ata5: hard resetting link
[ 1069.120536] ata6: exception Emask 0x50 SAct 0x0 SErr 0x4090800 action 0xe frozen
[ 1069.120540] ata6: irq_stat 0x00400040, connection status changed
[ 1069.120545] ata6: SError: { HostInt PHYRdyChg 10B8B DevExch }
[ 1069.120551] ata6: hard resetting link
[ 1074.140996] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 1074.155085] ata5.00: configured for UDMA/133
[ 1074.155092] ata5: EH complete
[ 1074.488246] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 1074.498546] ata6.00: configured for UDMA/133
[ 1074.498554] ata6: EH complete
[ 1074.795396] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 1074.827909] ata4.00: configured for UDMA/133
[ 1074.827916] ata4: EH complete
[ 1178.825085] ata5: exception Emask 0x10 SAct 0x0 SErr 0x4090000 action 0xe frozen
[ 1178.825091] ata5: irq_stat 0x00400040, connection status changed
[ 1178.825097] ata5: SError: { PHYRdyChg 10B8B DevExch }
[ 1178.825104] ata5: hard resetting link
[ 1178.825646] ata4: exception Emask 0x10 SAct 0x0 SErr 0x4090000 action 0xe frozen
[ 1178.825650] ata4: irq_stat 0x00400040, connection status changed
[ 1178.825655] ata4: SError: { PHYRdyChg 10B8B DevExch }
[ 1178.825660] ata4: hard resetting link
[ 1178.825758] ata6: exception Emask 0x50 SAct 0x0 SErr 0x4090800 action 0xe frozen
[ 1178.825762] ata6: irq_stat 0x00400040, connection status changed
[ 1178.825767] ata6: SError: { HostInt PHYRdyChg 10B8B DevExch }
[ 1178.825772] ata6: hard resetting link
[ 1183.842120] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 1183.860448] ata5.00: configured for UDMA/133
[ 1183.860456] ata5: EH complete
[ 1184.201753] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 1184.213180] ata6.00: configured for UDMA/133
[ 1184.213183] ata6: EH complete
[ 1184.512810] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 1184.541180] ata4.00: configured for UDMA/133
[ 1184.541184] ata4: EH complete
```

---

