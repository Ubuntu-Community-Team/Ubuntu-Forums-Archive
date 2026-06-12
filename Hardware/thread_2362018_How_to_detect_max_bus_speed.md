---
title: "How to detect max bus speed"
date: 2017-05-23
forum: Hardware
---

### Post by bandito40 on 2017-05-23
Looking to upgrade my hhd to a SSD and would like it to match the bus speed of my laptop. I have seen many posts on how to check ram speed but I am not sure that it is the same as the hhd speed. Either way big thanks to anyone who could let me know.

---

### Post by TheFu on 2017-05-23
These days the bus speeds are 20x faster than storage, unless you buy THE fastest SSDs, then the bus will be 8x faster.

The bus architecture and limitations will be in the motherboard designs. I don't know of any way to "test" or even get a report from the system about any limitations.

SATA-II - 3Gbps
SATA-III - 6Gpbs
USB2 - 480Mbps (I've never seen more than 240 Mbps from any USB2 device)
USB3 - 5Gpbs 

The fastest SSDs I've ever read about were 800-ish Mbps.  Cheap consumer SSDs are under 200 Mbps. You can't "match" the bus speed with storage.

However, the SATA specs are for the connection, not for what the actual motherboard bus can support.  I have a 2010 motherboard which can't support real-world USB3 storage. The internal motherboard architecture just wasn't designed for it.  I added a USB3 card to the system and the internal bus just can't handle it.

Even with all of that being said, it is possible to connect fast storage to a slow port on your computer.  Connecting a USB3 device to a USB2 port won't get faster than USB2.  In my testing USB3 devices **are** a little faster than USB2 devices, but still closer to the USB2 device performance than USB3. USB3 storage connected to USB2 ports might get 35MBps.  I'm being careful between MBps and Mbps.

```
$ lsusb -t
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 5000M
    |__ Port 2: Dev 2, If 0, Class=Hub, Driver=hub/4p, 5000M
        |__ Port 1: Dev 4, If 0, Class=Hub, Driver=hub/4p, 5000M
            |__ Port 2: Dev 5, If 0, Class=Mass Storage, Driver=usb-storage, 5000M
    |__ Port 4: Dev 3, If 0, Class=Mass Storage, Driver=usb-storage, 5000M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/1p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/4p, 480M
        |__ Port 2: Dev 3, If 0, Class=Hub, Driver=hub/4p, 480M
            |__ Port 1: Dev 4, If 0, Class=Hub, Driver=hub/4p, 480M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/8p, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/6p, 480M
```
This command shows the reported USB speeds. They are all lies, but connecting a USB2 device to a USB3 port will never achieve USB3 speeds. As you can see, there are 2 USB3 storage devices connected above.  I'll run a test on one of the storage devices. It is a 4+ yr old 2TB external disk.

1 laptop here has an m2.SSD.  This test took just under 8min to run:
```
$ bonnie++ -d . -m cc3550 -r 4000M
Version  1.97       ------Sequential Output------ --Sequential Input- --Random-
Concurrency   1     -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
cc3550           8G   850  98 36972   2 41396   3  3366  99 304741  10 15615 114
Latency             10473us   11097ms    5491ms    8188us   59448us   12801us
Version  1.97       ------Sequential Create------ --------Random Create--------
cc3550              -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++
Latency               838us     442us     473us     659us      21us     998us
```
Hopefully, everything will line up. K/sec is KB/sec according to the manpage.  36MB/sec.  Nowhere near theoretical SATA2, SATA3 or USB3 bus speeds.  Even the block reads were under 300 MB/sec.  The modern specs for SATA and USB3 left plenty of room for 4 disk systems.  Just sayin'.

---

### Post by bandito40 on 2017-05-23
Looks like you answer my question.  The drive will be internal so if you are saying that an SSD doesn't operate faster then the connection/bus speed then any SSD will work.

---

### Post by TheFu on 2017-05-23
If the SSD uses SATA2 or SATA3, then I wouldn't worry.  On some laptops, the internal devices use USB2, but not for the main storage. For example, some internal wifi/bluetooth stuff uses USB internally.

If you really want to be certain, you'll need to get the motherboard specs and hopefully an architecture diagram that shows internal bus architecture for it.  Not all manufacturers provide that.
For example: [http://www.gigabyte.com/Motherboard/GA-Z170X-Designare-rev-10#sp](http://www.gigabyte.com/Motherboard/GA-Z170X-Designare-rev-10#sp) - no diagram, but they specify the chipset, so you can look that up on Intel's site with a reference design. [https://ark.intel.com/products/90591/Intel-Z170-Chipset](https://ark.intel.com/products/90591/Intel-Z170-Chipset)  and I stopped looking there.  I don't own a Z170, so this isn't interesting to me.

---

### Post by Yellow Pasque on 2017-05-24
If you're replacing a hard disk, get a SATA 6Gbps SSD (most SATA SSD's being sold nowadays are 6Gbps anyway). Even if your laptop only supports SATA 3Gbps, SATA is backwards compatible.

---

