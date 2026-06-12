---
title: "Looking to buy a scanner..."
date: 2009-11-16
forum: Hardware
---

### Post by shortmort37 on 2009-11-16
I've recently installed 9.10 -- and, I'm looking to buy a scanner. In the online documentation, I read:
 
"Simply plug it in and try it! If it is a newer Universal Serial Bus (USB) scanner, it is likely that it will just work".
 
...but that doesn't seem to jive with other stuff I've been reading; like, the supported scanners linked to on the same page:
 
[https://wiki.ubuntu.com/HardwareSupportComponentsScanners](https://wiki.ubuntu.com/HardwareSupportComponentsScanners)
 
There seems to be a whole lotta stuff that just doesn't work. I read the same thing on the Sane website; I'm attracted to the new Canon LiDE 200, but I'm reading horror stories about it with linux. And, why should I pay a premium price for a scanner that works with Ubuntu, simply because it's used and it's old?
 
So here's the question: Does anyone make a flatbed scanner sleek as the LiDE series, that's new, works with Ubuntu (with the complete feature set), and is comparable in price? I'm ready to sign up, just... tired of searching.
 
adTHANKSvance,
Dan

---

### Post by boba1120 on 2009-11-17
I feel your pain Dan, scant hardware support is the biggest challenge to Linux desktop adoption I think.  I've personally struggled with "FakeRAID" support as well as Creative sound cards, it definitely is exhausting.  And I agree, the happy-go-lucky "just plug it in and see!" line isn't very comforting.

In regards to your particular headache, I've tried to pick up where you left off the search, and I have some ideas.  For one, the Ubuntu support list is a little weak, it looks largely user-driven and not well trafficked.  For a more complete view I'd recommend going to the source which is: [http://www.sane-project.org/]("http://www.sane-project.org/").

Here you'll find up to date lists.  You'll see that Canon is not well represented for anything fairly recent.  HP I'm told is the most Linux friendly of the major manufacturers, but they aren't well-liked for scanning as far as I can tell.  This leaves Epson; it looks like the V30 and V300 are in the ballpark of what you're looking for, and while SANE lists them as unsupported the links lead you here: [http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do]("http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do")

I don't have any personal experience with AVASYS, but they appear to have a clear and cohesive offering for the Epson products, with distribution specific downloads available.  I'm not a license expert, but at a glance it looks like they're only "Free as in Beer', which may explain why they're only linked from SANE and not really mentioned in Ubuntu support.

I'd be curious to hear from anyone that's worked with these drivers, and what their experience was.  It'd be nice to have a vote of confidence before shelling out the cash on new hardware!

---

### Post by shortmort37 on 2009-11-17
Well, the V30 looks attractive -- it's new, it's sleek, it's inexpensive.
 
...but it's apparently not without it's problems, even with avasys:
 
[http://ubuntuforums.org/showthread.php?t=1286162&highlight=V30](http://ubuntuforums.org/showthread.php?t=1286162&highlight=V30)
 
I'm tempted to buy it, and wait for this to sort itself out with a patch down the line (since, apparently there aren't any microcode issues).  On the other hand, mebbe I'll just wait.
 
Dan

---

### Post by shortmort37 on 2009-12-23
Well, I waited long enough.  I bought the V30.  But now I have another problem...

I've also got a PCI ATI All-in-Wonder video digitizer card (that's another story). lspci -vv says this about the ATI:

11:00.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
Subsystem: ATI Technologies Inc Device 0003
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 132 (4000ns min, 10000ns max)
Interrupt: pin A routed to IRQ 20
Region 0: Memory at fc800000 (32-bit, prefetchable) [size=4K]
Kernel driver in use: bttv
Kernel modules: bttv

When I launch XSane, it scans for devices, and preferentially chooses the All-in-Wonder.  Upon exit, it creates a drc file with this name:

Noname:BT878video(ATITV-WonderVE).drc

Here are the contents:

"XSANE_DEVICE_RC"
"Noname:BT878 video (ATI TV-Wonder VE)"
"xsane-version"
"0.996"
"mode"
"Gray"
"channel"
"Television"
"brightness"
128
[snip]

I presume I want to create another drc file I can choose (Preferences -> load device settings) that describes the V30 -- but, what should the contents be?  The contents of the ATI drc bears little semblance to the information in the lspci output.  What is it in the drc that XSane uses to choose the device?

Also, I don't get the relation between the drc file, and the conf files in /etc/sane.d.  It would be easy enough for me to edit epson.conf with the product and device ID, but what chooses that file as opposed to, say, artec.conf?

For completeness, I follow with the lsusb -vv for the V30.

adTHANKSvance,
Dan

Bus 001 Device 002: ID 04b8:0131 Seiko Epson Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0        64
  idVendor           0x04b8 Seiko Epson Corp.
  idProduct          0x0131 
  bcdDevice            1.00
  iManufacturer           1 EPSON
  iProduct                2 EPSON Scanner
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower                2mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval             255
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval             255
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered

---

### Post by shortmort37 on 2009-12-24
OMG -- I...  forgot.

I loaded the driver from here:

[http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do)

Rebooted, and it worked like a champ.

Here's a review:

[http://www.hawkee.com/shop/review/424404/](http://www.hawkee.com/shop/review/424404/)

Dead-on.  If you're looking for an inexpensive scanner that works with Ubuntu, get the Epson V30, install the Avasys driver, and the whole thing's wired.

Dan

---

### Post by HappyFeet on 2009-12-24
> **shortmort37 said:**
> If you're looking for an inexpensive scanner that works with Ubuntu, get the Epson V30

Or just buy an HP, and watch the plug n play magic happen.

---

### Post by shortmort37 on 2009-12-24
> **HappyFeet said:**
> Or just buy an HP, and watch the plug n play magic happen.

Oh, did I not say, inexpensive?  Mea maxima culpa :cool:

Dan

---

