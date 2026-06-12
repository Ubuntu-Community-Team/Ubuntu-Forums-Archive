---
title: "USB3 external disk enclosure - not working at USB 3 &quot;SuperSpeed&quot;?"
date: 2010-12-10
forum: Hardware
---

### Post by cazabon on 2010-12-10
Edit:  I should have noted originally - I'm running 64-bit Lucid with a few-weeks-old mainline kernel from the Ubuntu mainline kernels [http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/daily/").

Summary:  USB 3 enclosure and controller appears to only be running at USB 2 speeds for unknown reasons.

I recently purchased a USB3 multi-drive enclosure (supports 4 SATA disks) and originally had it connected to a USB 2 port as I didn't have a USB 3 controller.  It worked much like every other external drive enclosure, and I would get roughly 30MB/s transfer from any of the drives in it when doing sequential reads with `hdparm -t`, about as expected for USB 2.  The drives can natively do much faster - when connected directly to the motherboard's SATA controllers, they're capable of 90-120MB/s.

The USB 3 controller arrived (it's a PCIe-x1 card based on the common NEC chip) and I have since moved the enclosure over to one of the two USB 3 ports provided by the card.  But performance hasn't changed - I'm still seeing roughly 30MB/s reads from any of the drives.  If I read from all four at once, the total transfer again tops out at roughly 30MB/s.

It looks to me like the enclosure is for some reason still using USB 2 "high speed", 480Mbps, not the USB 3 "SuperSpeed" 4.8Gbps.  I don't know why this is - the enclosure is supposed to support SuperSpeed and came with a USB 3 cable which I'm using to connect it to the USB 3 controller.

`lspci` shows the USB 3 controller:
```
03:00.0 USB Controller: NEC Corporation Device 0194 (rev 03) (prog-if 30)
        Subsystem: NEC Corporation Device 0194
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at fdefe000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: [50] Power Management version 3
        Capabilities: [70] Message Signalled Interrupts: Mask- 64bit+ Queue=0/3 Enable-
        Capabilities: [90] MSI-X: Enable+ Mask- TabSize=8
        Capabilities: [a0] Express Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [140] Device Serial Number ff-ff-ff-ff-ff-ff-ff-ff
        Capabilities: [150] #18
        Kernel driver in use: xhci_hcd
        Kernel modules: xhci-hcd

````lsusb -v` shows the machine identifies it as a USB 3.0 root hub, and the attached enclosure as a USB-to-ATA bridge based on a JMicron chip:
```
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               3.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         3 
  bMaxPacketSize0         9
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0003 3.0 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.36-999-generic xhci_hcd
  iProduct                2 xHCI Host Controller
  iSerial                 1 0000:03:00.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             4
  wHubCharacteristic 0x0009
    Per-port power switching
    Per-port overcurrent protection
    TT think time 8 FS bits
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0503 highspeed power enable connect
   Port 4: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 008 Device 002: ID 152d:0551 JMicron Technology Corp. / JMicron USA Technology Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x152d JMicron Technology Corp. / JMicron USA Technology Corp.
  idProduct          0x0551 
  bcdDevice            1.00
  iManufacturer           1 JMicron
  iProduct                2 USB to ATA/ATAPI Bridge
  iSerial                 5 DCAA1929286F
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 USB Mass Storage
    bmAttributes         0xc0
      Self Powered
    MaxPower                2mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              6 MSC Bulk-Only Transfer
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered

```kern.log shows the system detecting this controller and assigning it USB bus #8, but it looks to me like it is indeed using USB 2 "high speed" - note the message "usb 8-3: new high speed USB device using xhci_hcd and address 0".
```
[   22.231098] xhci_hcd 0000:03:00.0: PCI INT A
 -> GSI 17 (level, low) -> IRQ 17
[   22.231129] xhci_hcd 0000:03:00.0: setting latency timer to 64
[   22.231132] xhci_hcd 0000:03:00.0: xHCI Host Controller
[   22.231201] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 8
[   22.231310] xhci_hcd 0000:03:00.0: irq 17, io mem 0xfdefe000
[   22.231344]   alloc irq_desc for 42 on node 0
[   22.231346]   alloc kstat_irqs on node 0
[   22.231352] xhci_hcd 0000:03:00.0: irq 42 for MSI/MSI-X
[   22.231354]   alloc irq_desc for 43 on node 0
[   22.231355]   alloc kstat_irqs on node 0
[   22.231358] xhci_hcd 0000:03:00.0: irq 43 for MSI/MSI-X
[   22.231359]   alloc irq_desc for 44 on node 0
[   22.231361]   alloc kstat_irqs on node 0
[   22.231363] xhci_hcd 0000:03:00.0: irq 44 for MSI/MSI-X
[   22.231365]   alloc irq_desc for 45 on node 0
[   22.231366]   alloc kstat_irqs on node 0
[   22.231368] xhci_hcd 0000:03:00.0: irq 45 for MSI/MSI-X
[   22.231370]   alloc irq_desc for 46 on node 0
[   22.231371]   alloc kstat_irqs on node 0
[   22.231373] xhci_hcd 0000:03:00.0: irq 46 for MSI/MSI-X
[   22.234672] usb usb8: No SuperSpeed endpoint companion for config 1  interface 0 altsetting 0 ep 129: using minimum values
[   22.234737] xHCI xhci_add_endpoint called for root hub
[   22.234739] xHCI xhci_check_bandwidth called for root hub
[   22.234763] hub 8-0:1.0: USB hub found
[   22.234767] hub 8-0:1.0: 4 ports detected
[   22.450593] EXT3-fs (md1): using internal journal
[   22.550336] usb 8-3: new high speed USB device using xhci_hcd and address 0
[   22.573462] xhci_hcd 0000:03:00.0: WARN: short transfer on control ep
[   22.574155] xhci_hcd 0000:03:00.0: WARN: short transfer on control ep
[   22.574931] xhci_hcd 0000:03:00.0: WARN: short transfer on control ep
[   22.575675] xhci_hcd 0000:03:00.0: WARN: short transfer on control ep
[   22.576899] xhci_hcd 0000:03:00.0: WARN: short transfer on control ep
[   22.577835] xhci_hcd 0000:03:00.0: WARN: short transfer on control ep
[   22.797048] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   22.827819] Initializing USB Mass Storage driver...
[   22.828050] scsi12 : usb-storage 8-3:1.0
[   22.828153] usbcore: registered new interface driver usb-storage
[   22.828155] USB Mass Storage support registered.

```So ... can anyone help determine (a) if I'm right and this enclosure is, for some reason, talking to the USB 3 controller at USB 2 speeds, and (b) if so, how to correct this?

Any help appreciated - thanks.

Charles

---

### Post by cazabon on 2010-12-17
Solved this myself - for the benefit of others with similar problems, here's the answer.

It's a kernel bug in the USB 3 code.  The USB xhci driver was disabling the USB 3 port in such a way that it couldn't detect a SuperSpeed device, so that when the device was connected it was only detected as a High-Speed (480Mbps, USB 2 speed) device.

The fix appears to have gone into the kernel in version 2.6.37-rc5, in commit 435a5aebf609624bdf7c5a9a7705c260d0076195 - see the [changelog]("http://www.kernel.org/pub/linux/kernel/v2.6/testing/ChangeLog-2.6.37-rc5") for details.

With a nighly mainline kernel from after -rc5, I see the following correct log message when the device is attached:

```
kernel: [  458.500437] usb 8-1: new SuperSpeed USB device using xhci_hcd and address 2
```

I hope this helps someone.

Charles

---

### Post by insaini on 2011-03-09
I installed the latest 2.6.36 rc8

can you tell me if this includes that patch ?

---

### Post by soborobo on 2011-12-01
Thanks a lot Charles!

I hope that this new xhci_hcd driver makes it into the LTS 10.04 Ubuntu!

Please reply when this is done.

Thanks to all!

---

### Post by soborobo on 2011-12-05
We have just upgraded to Linux 2.6.32-36-generic #79-Ubuntu

and still nothing yet :(

Merry Christmas to all!

--Ralph

---

### Post by Mark Phelps on 2011-12-05
Is there some problem with understanding the simple statement:

> The fix appears to have gone into the kernel in version 2.6.37-rc5

So ... 2.6.32-36-generic and 2.6.36 rc8 are not NEW enough.

Good grief folks ... learn how to read.

---

### Post by soborobo on 2011-12-06
No, just that version 2.6.37-rc5 is NOT lts!

So for the moment, important patches should be _back _ported to Lucid 10.04 LTS!

That's all! :icon_frown:,

--RS

---

