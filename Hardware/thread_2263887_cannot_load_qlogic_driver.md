---
title: "cannot load qlogic driver"
date: 2015-02-04
forum: Hardware
---

### Post by ikki_72 on 2015-02-04
package linux-firmware installed
ubuntu 14.04 64-bit

```
$ sudo grep qla /var/log/dmesg
[    3.456090] qla2xxx [0000:00:00.0]-0005: : QLogic Fibre Channel HBA Driver: 8.06.00.08-k.
[    3.456261] qla2xxx [0000:11:00.0]-001d: : Found an ISP2532 irq 32 iobase 0xffffc900135aa000.
[    3.548710] qla2xxx 0000:11:00.0: irq 110 for MSI/MSI-X
[    3.548718] qla2xxx 0000:11:00.0: irq 111 for MSI/MSI-X
[    6.234796] qla2xxx 0000:11:00.0: Direct firmware load failed with error -2
[    6.242508] qla2xxx 0000:11:00.0: Falling back to user helper
[    6.250812] qla2xxx [0000:11:00.0]-0063:1: Failed to load firmware image (ql2500_fw.bin).
[    6.258804] qla2xxx [0000:11:00.0]-0090:1: Fimware image unavailable.
[    6.266685] qla2xxx [0000:11:00.0]-0091:1: Firmware images can be retrieved from: http://ldriver.qlogic.com/firmware/.
[    7.059579] qla2xxx [0000:11:00.0]-1020:1: **** Failed mbx[0]=4006, mb[1]=907, mb[2]=6cee, mb[3]=9100, cmd=59 ****.
[    7.067860] scsi1 : qla2xxx
[    7.076129] qla2xxx [0000:11:00.0]-00fb:1: QLogic QLE2560 - QLogic 8Gb FC Single-port HBA for System x.
[    7.084577] qla2xxx [0000:11:00.0]-00fc:1: ISP2532: PCIe (5.0GT/s x8) @ 0000:11:00.0 hdma+ host#=1 fw=5.03.06 (80).
[    7.093228] qla2xxx [0000:20:00.0]-001d: : Found an ISP2532 irq 42 iobase 0xffffc90013590000.
[    7.101972] qla2xxx 0000:20:00.0: irq 149 for MSI/MSI-X
[    7.101979] qla2xxx 0000:20:00.0: irq 150 for MSI/MSI-X
[    7.880033] qla2xxx [0000:11:00.0]-505f:1: Link is operational (8 Gbps).
[    7.911110] qla2xxx [0000:11:00.0]-2064:1: SNS scan failed -- assuming zero-entry result.
[    9.654127] qla2xxx 0000:20:00.0: Direct firmware load failed with error -2
[    9.662726] qla2xxx 0000:20:00.0: Falling back to user helper
[    9.671670] qla2xxx [0000:20:00.0]-0063:8: Failed to load firmware image (ql2500_fw.bin).
[    9.680363] qla2xxx [0000:20:00.0]-0090:8: Fimware image unavailable.
[    9.688991] qla2xxx [0000:20:00.0]-0091:8: Firmware images can be retrieved from: http://ldriver.qlogic.com/firmware/.
[   10.482914] qla2xxx [0000:20:00.0]-1020:8: **** Failed mbx[0]=4006, mb[1]=907, mb[2]=6c15, mb[3]=7100, cmd=59 ****.
[   10.491888] scsi8 : qla2xxx
[   10.500916] qla2xxx [0000:20:00.0]-00fb:8: QLogic QLE2560 - QLogic 8Gb FC Single-port HBA for System x.
[   10.509908] qla2xxx [0000:20:00.0]-00fc:8: ISP2532: PCIe (5.0GT/s x8) @ 0000:20:00.0 hdma+ host#=8 fw=5.03.06 (80).
[   11.301490] qla2xxx [0000:20:00.0]-505f:8: Link is operational (8 Gbps).
[   11.331464] qla2xxx [0000:20:00.0]-2064:8: SNS scan failed -- assuming zero-entry result.
```

how can I make ql2500_fw.bin loaded?

```
$ ls /lib/firmware/ql2*
/lib/firmware/ql2100_fw.bin  /lib/firmware/ql2322_fw.bin
/lib/firmware/ql2200_fw.bin  /lib/firmware/ql2400_fw.bin
/lib/firmware/ql2300_fw.bin  /lib/firmware/ql2500_fw.bin
```

---

