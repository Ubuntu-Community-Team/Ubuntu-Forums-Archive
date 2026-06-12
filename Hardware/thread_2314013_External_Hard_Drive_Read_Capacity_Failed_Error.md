---
title: "External Hard Drive Read Capacity Failed Error"
date: 2016-02-17
forum: Hardware
---

### Post by cater2 on 2016-02-17
Hi, 

I have an External Hard Drive with issues mounting to Ubuntu 14.04. I have ran lsusb and the hard drive has not been detected however dmesg does show the hard drive. Below is the output from dmesg (I removed the hard drive from the external usb hard drive enclosure so the output will show it as a SATA drive.) Thanks.  

[922952.903966] ata5: exception Emask 0x10 SAct 0x0 SErr 0x4050002 action 0xe frozen
[922952.903969] ata5: irq_stat 0x00000040, connection status changed
[922952.903970] ata5: SError: { RecovComm PHYRdyChg CommWake DevExch }
[922952.903974] ata5: hard resetting link
[922958.668487] ata5: link is slow to respond, please be patient (ready=0)
[922962.926452] ata5: COMRESET failed (errno=-16)
[922962.926457] ata5: hard resetting link
[922968.693114] ata5: link is slow to respond, please be patient (ready=0)
[922972.951078] ata5: COMRESET failed (errno=-16)
[922972.951083] ata5: hard resetting link
[922978.717738] ata5: link is slow to respond, please be patient (ready=0)
[922981.855188] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[922981.855660] ata5.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x80)
[922986.857495] ata5: hard resetting link
[922992.219965] ata5: link is slow to respond, please be patient (ready=0)
[922996.870108] ata5: COMRESET failed (errno=-16)
[922996.870113] ata5: hard resetting link
[923002.232580] ata5: link is slow to respond, please be patient (ready=0)
[923006.882729] ata5: COMRESET failed (errno=-16)
[923006.882733] ata5: hard resetting link
[923012.245198] ata5: link is slow to respond, please be patient (ready=0)
[923040.370181] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[923040.370660] ata5.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x80)
[923040.370662] ata5: limiting SATA link speed to 1.5 Gbps
[923045.372482] ata5: hard resetting link
[923050.734953] ata5: link is slow to respond, please be patient (ready=0)
[923055.385098] ata5: COMRESET failed (errno=-16)
[923055.385103] ata5: hard resetting link
[923060.747570] ata5: link is slow to respond, please be patient (ready=0)
[923065.397712] ata5: COMRESET failed (errno=-16)
[923065.397717] ata5: hard resetting link
[923070.760189] ata5: link is slow to respond, please be patient (ready=0)
[923084.038320] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[923084.038802] ata5.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x80)
[923089.040619] ata5: hard resetting link
[923094.403092] ata5: link is slow to respond, please be patient (ready=0)
[923099.053234] ata5: COMRESET failed (errno=-16)
[923099.053239] ata5: hard resetting link
[923104.415707] ata5: link is slow to respond, please be patient (ready=0)
[923109.065853] ata5: COMRESET failed (errno=-16)
[923109.065859] ata5: hard resetting link
[923114.428327] ata5: link is slow to respond, please be patient (ready=0)
[923138.015215] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[923138.031215] ata5: EH complete

---

