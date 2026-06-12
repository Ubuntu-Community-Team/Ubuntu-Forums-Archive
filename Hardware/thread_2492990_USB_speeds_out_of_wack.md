---
title: "USB speeds out of wack"
date: 2023-11-29
forum: Hardware
---

### Post by drigi19862 on 2023-11-29
Hi peeps!

I am running Ubuntu server from mini PC (specs are [HERE]("https://icecat.biz/p/hp/f6x31et/elitedesk-pcs-workstations-0888793005408-800+g1-29910572.html")) 

I have been checking my USB speeds because I want to connect multiple drives to it. In my computer specs it says I have 6 x USB 3.2 Gen 1 (3.1 Gen 1) Type-A ports. Now after running lsusb, I see only TWO usb 3.2 ports capable of 5 Gbps.

```
 lsusb -t
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/6p, 5000M
    |__ Port 2: Dev 2, If 0, Class=Mass Storage, Driver=uas, 5000M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/15p, 480M
    |__ Port 1: Dev 2, If 0, Class=Mass Storage, Driver=uas, 480M
    |__ Port 2: Dev 3, If 0, Class=Mass Storage, Driver=usb-storage, 480M
    |__ Port 6: Dev 4, If 0, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 6: Dev 4, If 1, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 6: Dev 4, If 2, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 13: Dev 5, If 0, Class=Mass Storage, Driver=uas, 480M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/3p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/8p, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/3p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/6p, 480M

```

Obvious issue: 
    Why does lsusb list only 2 x USB 3 when I the computer should have 6? I have also measured it's speeds and it does not come even close to USB 3 but rather USB 2.

---

### Post by TheFu on 2023-11-29
Are there connectors inside the case?

BTW, those speeds aren't true.  They are theoretical bus speeds only.  The actual performance will be dependent on the true performance of the actual devices on the bus.  Also, if multiple devices are on the same shared bus, the limitation will be shared across all of them.

For example, with USB2 the bus claims to support 480 Mbps (60 MBps), but about 22MBps is the best I've gotten with spinning rust storage.  Bits vs Bytes.  A typical SATA SSD might provide 550 Mbps.  So, connection to a USB3 5000 Mbps bus really doesn't matter.  Also, USB storage performance isn't as tight as SATA, eSATA, SCSI, SAS and dedicated storage protocols.  Always prefer those over USB storage connections. The protocols for real storage are noticeably better, in multiple ways, than the 2 USB storage protocols.

I don't want to say there isn't anything that can be done, just that expectations for the entire chain of transfer not just the USB3 bus need to be considered.  Don't forget that the PCIe bus matters and may limit performance, especially since most desktops will share that PCIe bus with other onboard devices - the GPU, the NIC(s), and other PCIe slots.

So, when we look at your tree, we see only 1 bus has USB3 specs.  If you connect 2 devices, they will share the real max.  In theory, each bus can support 128 USB devices, but it seldom actually works out well.

---

### Post by drigi19862 on 2023-11-29
My hard drives are inside [QNAP-TR004]("https://www.qnap.com/en/product/tr-004") with SATA connectors for HDD with Ironfolw for drives themselves.

I understand the speed issue generally but what is frustrating is that speeds are sometimes not close to even USB 2. My measured speed using ```
sudo dd if=/dev/zero of=/mnt/qnap/testfile bs=1M count=1000 oflag=dsync
``` is from 10 and 100 MB/s, so 800 Mbps max.

I am struggling to understand also how is it possible that HP is saying there should be 6 x USB 3 ports when there are only 2? Wait, does in above post actually say 2 or only one?

Frankly I am at a bit of a loss and am trying to wrap my head around what is happening.

If you have any ideas or conjectures, let me know. I will in the mean time continue trying different ports so I have a full picture.

---

### Post by Yellow Pasque on 2023-11-30
lsusb can be a bit hard to decipher. The key is that you have xhci used for the hubs, so that indicates 3.x capability. You also have ehci hubs, but I suspect those are part of the Q87 chipset and not physically connected to anything.
Sorry I can't offer anything more practical..

---

### Post by drigi19862 on 2023-12-04
Thanks anyway, I will be looking into buying a mini computer specifically designed for linux.

---

