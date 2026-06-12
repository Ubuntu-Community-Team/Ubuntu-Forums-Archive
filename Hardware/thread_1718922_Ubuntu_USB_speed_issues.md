---
title: "Ubuntu USB speed issues"
date: 2011-04-01
forum: Hardware
---

### Post by jiapei100 on 2011-04-01
Hi, all:

OS Environment: Ubuntu 10.10 .
What's more, I believe I've got 4 USB2.0 ports.

I'm backing up a huge amount of data from one external hard drive A to the other external hard drive B. The average backup speed is around 3.0mega bytes per second (3M/s), and I really can't bear the backup speed any longer. 

I found a post at
[http://ubuntuforums.org/archive/index.php/t-977043.html](http://ubuntuforums.org/archive/index.php/t-977043.html)
, then I tried the following command:
```
$ lspci | grep -i usb
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
$ hwinfo | grep usb.version
  usb.version = 2.00000
  usb.version = 2.00000
  usb.version = 2.00000
  usb.version = 2.00000
  usb.version = 2.00000
  usb.version = 2.00000
  usb.version = 2.00000
  usb.version = 1.10000
  usb.version = 1.10000
  usb.version = 1.10000
  usb.version = 1.10000
  usb.version = 1.10000

```

It looks like Ubuntu 10.10 treats my 4 USB 2.0 ports as USB 1.1 ones. As you may notice, the first 4 USB Controllers are USB UHCI, instead of USB2 EHCI.

I first do
```
$ modprobe -l | grep "hci"
kernel/drivers/ata/ahci.ko
kernel/drivers/ata/libahci.ko
kernel/drivers/ata/ahci_platform.ko
kernel/drivers/ieee1394/ohci1394.ko
kernel/drivers/usb/host/whci/whci-hcd.ko
kernel/drivers/usb/host/xhci-hcd.ko
kernel/drivers/mmc/host/sdhci.ko
kernel/drivers/mmc/host/sdhci-pci.ko
kernel/drivers/mmc/host/sdhci-pltfm.ko
kernel/drivers/staging/usbip/vhci-hcd.ko
kernel/drivers/firewire/firewire-ohci.ko
kernel/drivers/uwb/whci.ko
kernel/drivers/bluetooth/hci_vhci.ko
kernel/drivers/bluetooth/hci_uart.ko

```
, in which there is nothing about "uhci".

Furthermore, my BIOS is R1.04 
```
$sudo dmidecode -s bios-version
R1.04
```
, there seems to be no place for me to choose "activate USB2" in R1.04 BIOS.

What can I do to speed up my backup between 2 external hard drives?


Thank you very much.

Best Regards
JIA

---

