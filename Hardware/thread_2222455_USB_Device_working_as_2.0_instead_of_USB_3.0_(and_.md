---
title: "USB Device working as 2.0 instead of USB 3.0 (and xhci_hcd not loaded)"
date: 2014-05-06
forum: Hardware
---

### Post by davidonlaptop on 2014-05-06
Hi,

I just bought a [SDD that came with a USB enclosure]("http://www.amazon.com/Kingston-Digital-2-5-Inch-SV300S37A-120G/dp/B00A1ZTZOG") and I am having trouble getting it to work with USB 3.0. I cannot find any spec about the enclosure, but I am assuming that it is USB 3.0. The 

The SSD runs at 35 MB/s (USB 2.0 speed) with hdparm -t when plugged on USB and at 490 MB/s when plugged on SATA.

Articles online suggest that I should be using the xhci_hcd module but it does not appear to be loaded even though I have a USB 3.0 port:

```
david@zalman:~/tmp$ sudo lspci |grep "SuperSpeed USB"
02:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
david@zalman:~/tmp$ sudo lsmod |grep hci
ahci                   25731  7 
libahci                31364  1 ahci
```

Should the xhci_hcd module be loaded at all time?

The /var/log/dmesg mentions xhci_hcd but no errors:
```
david@Zalman:~/tmp$ grep -riIn xhci /var/log/dmesg
643:[    1.333002] xhci_hcd 0000:02:00.0: xHCI Host Controller
644:[    1.333006] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 8
645:[    1.337401] xhci_hcd 0000:02:00.0: irq 72 for MSI/MSI-X
646:[    1.337406] xhci_hcd 0000:02:00.0: irq 73 for MSI/MSI-X
647:[    1.337411] xhci_hcd 0000:02:00.0: irq 74 for MSI/MSI-X
648:[    1.337415] xhci_hcd 0000:02:00.0: irq 75 for MSI/MSI-X
649:[    1.337420] xhci_hcd 0000:02:00.0: irq 76 for MSI/MSI-X
652:[    1.337482] usb usb8: Product: xHCI Host Controller
653:[    1.337483] usb usb8: Manufacturer: Linux 3.8.0-26-generic xhci_hcd
655:[    1.337543] xHCI xhci_add_endpoint called for root hub
656:[    1.337545] xHCI xhci_check_bandwidth called for root hub
659:[    1.337600] xhci_hcd 0000:02:00.0: xHCI Host Controller
660:[    1.337602] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 9
663:[    1.337624] usb usb9: Product: xHCI Host Controller
664:[    1.337626] usb usb9: Manufacturer: Linux 3.8.0-26-generic xhci_hcd
666:[    1.337668] xHCI xhci_add_endpoint called for root hub
667:[    1.337669] xHCI xhci_check_bandwidth called for root hub
```

```
david@Zalman:~/tmp$ uname -a
Linux Zalman 3.8.0-26-generic #38-Ubuntu SMP Mon Jun 17 21:43:33 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
david@zalman:~/tmp$ cat /etc/lsb-release |grep DESCRIPTION
DISTRIB_DESCRIPTION="Ubuntu 13.04"
```

Is there a way to force load the module xhci_hcd ?

---

### Post by davidonlaptop on 2014-05-06
Here's the output when I hook the device

```
[ 4459.215494] usb 2-1: new high-speed USB device number 6 using ehci-pci
[ 4459.348705] usb 2-1: New USB device found, idVendor=11b0, idProduct=6298
[ 4459.348716] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 4459.348724] usb 2-1: Product: SNA-DC/U        
[ 4459.348730] usb 2-1: Manufacturer: Kingston
[ 4459.348735] usb 2-1: SerialNumber: 353030323642373734323032
[ 4459.349323] scsi13 : usb-storage 2-1:1.0
[ 4460.347555] scsi 13:0:0:0: Direct-Access     Kingston SNA-DC/U         1.08 PQ: 0 ANSI: 4
[ 4460.348930] sd 13:0:0:0: Attached scsi generic sg2 type 0
[ 4460.350040] sd 13:0:0:0: [sdb] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[ 4460.350820] sd 13:0:0:0: [sdb] Write Protect is off
[ 4460.350829] sd 13:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 4460.351539] sd 13:0:0:0: [sdb] No Caching mode page present
[ 4460.351551] sd 13:0:0:0: [sdb] Assuming drive cache: write through
[ 4460.357157] sd 13:0:0:0: [sdb] No Caching mode page present
[ 4460.357168] sd 13:0:0:0: [sdb] Assuming drive cache: write through
[ 4460.361170]  sdb: sdb1
[ 4460.364646] sd 13:0:0:0: [sdb] No Caching mode page present
[ 4460.364656] sd 13:0:0:0: [sdb] Assuming drive cache: write through
[ 4460.364664] sd 13:0:0:0: [sdb] Attached SCSI disk
```

So does this output means the enclosure (or cable) is only USB 2.0, or could there be a config issue?

And also I'd like understand if the xhci_hcd driver will only get loaded when a valid USB 3.0 device is plugged in, or should it be loaded by default ?

---

