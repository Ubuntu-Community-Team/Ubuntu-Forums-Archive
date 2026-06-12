---
title: "Belkin High Speed Docking Station - Video Issues"
date: 2008-12-24
forum: Hardware
---

### Post by doughold on 2008-12-24
I have a Dell XPS M1210 and used to use my Belkin High Speed Docking Station with Vista until I got fed up with the BSOD's I kept getting (even after repairs and re-installs). Nevertheless, I am extremely pleased with my new Ubuntu 8.10 setup with one exception. For whatever reason Ubuntu is not recognizing the video card associated with the Belkin High Speed Docking Station I have hooked up via the express card slot. Here is my LSPCI output:

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
```

Here is my LSUSB:

```
Bus 005 Device 010: ID 0711:0028 Magic Control Technology Corp. 
Bus 005 Device 009: ID 0d8c:0006 C-Media Electronics, Inc. Storm HP-USB500 5.1 Headset
Bus 005 Device 008: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 005 Device 007: ID 07a6:8515 ADMtek, Inc. AN8515 Ethernet
Bus 005 Device 006: ID 046d:c512 Logitech, Inc. LX-700 Cordless Desktop Receiver
Bus 005 Device 004: ID 046d:08c6 Logitech, Inc. QuickCam for DELL Notebooks
Bus 005 Device 003: ID 0424:2507 Standard Microsystems Corp. 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:8114 Dell Computer Corp. Wireless 5700 Mobile Broadband (CDMA EV-DO) Minicard Modem
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

I did a search on Magic Control Technology Corp and saw that they make USB to VGA adapters so I am assuming that is my external video card, however it is not being recognized by Ubuntu. Any thoughts?

---

### Post by doughold on 2008-12-30
--=BUMP=--

Thoughts anyone? This is the only thing keeping me from moving to Ubuntu full time.

---

### Post by x20mar on 2009-01-10
Hi sorry this is a bit off topic but did the Belkin High-Speed Docking Station work fully apart from the video output?

Please let me know as I'm considering purchasing one myself

Thanks

---

### Post by doughold on 2009-01-13
I only use it for it's USB hub, fiber audio out and (hopefully) video. That being said, everything else works like a charm. Though I would recommend installing the Pulse Audio software to manage your audio streams. You can switch between output devices in real time. I find this useful when I am unplugging my laptop from my docking station. With vista you have to set the default audio, then close all audio streams and restart them so that was a nice feature for me to have.

---

### Post by Tuxor on 2009-04-22
Hi,
I have the same docking station and have found a solution a while ago. You can look at this thread:
[http://ubuntuforums.org/showthread.php?p=4711410#post4711410](http://ubuntuforums.org/showthread.php?p=4711410#post4711410)

I have extended the solution described there so a startup script automatically recognizes if the laptop is docked, and sets the correct xorg.conf. This was done by adding the script using Debians standard procedure with the **update-rc.d** shell command. Look for more details with **man update-rc.d**.

I put my script as *S20dock-mode* in the folder */etc/rc2.d*.

The script is in the attached file.

---

### Post by emmbea on 2009-12-29
Hi,
I have the same docking station but no luck with setting up video yet.
Have you guys got it working since the last post?
The Volari card doesn't show up in my lspci output, so the pointer towards the sis driver did not work out for me. I don't know if the assumption that the device below would be the video card is correct.
```
lsusb
Bus 001 Device 007: ID 0711:0028 Magic Control Technology Corp. 
```It is recognized as a human interface device.
```
dmesg
...
[    3.218257] generic-usb 0003:0711:0028.0004: hiddev96,hidraw1: USB HID v1.10 Device [MCT Corp_ Dock 01] on usb-0000:00:1a.7-2.7.2/input0
...
``````
lsusb -vd 0711:0028
Bus 001 Device 007: ID 0711:0028 Magic Control Technology Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0711 Magic Control Technology Corp.
  idProduct          0x0028 
  bcdDevice            2.01
  iManufacturer           1 
  iProduct                3 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           41
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
      ** UNRECOGNIZED:  09 21 10 01 00 01 22 19 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
```All the other ports are working perfectly, this is the only thing missing from my dock-wise happiness. (I'm running Karmic on a Dell Vostro 1015.)
Any thoughts on this?
Thanks.

---

### Post by lindude on 2010-01-13
Is there an easy way for a newbie to get this to work with 9.10?

I had a look at this link "http://ubuntuforums.org/showthread.p...10#post4711410" from above, way above my head.

I'm using an older machine, a Dell XPS M1210.
Thanks

---

### Post by emmbea on 2010-03-05
After some experiments it turns out that the video card is indeed a PCI device. It shows up when booting with the connector plugged in mode "A".
The lspci goes:
```
0e:02.0 VGA compatible controller: XGI Technology Inc. (eXtreme Graphics Innovation) Z7/Z9 (XG20 core)
```

Went on with setting up switchconf as Tuxor suggested. All was fine except the second card couldn't be initialized properly.
See this bug: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/430919](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/430919)
The only difference is that in my case it is not possible to set the primary card other than the one inside the laptop in the BIOS.

---

### Post by shiva_SVK on 2010-03-14
I was looking for some informations about the graphic card used and I came upon this site, where you can download Linux drivers for Z9s (version with VGA + DVI outptu): [http://www.xgitech.com/sd/sd_download3.asp?CTID={F4BB00F8-E5A7-4DAE-9F83-6E506605567D}&PType_3={54EF6C90-A1A5-47CA-8E49-C5C64D4C82E8}]("http://www.xgitech.com/sd/sd_download3.asp?CTID=%7BF4BB00F8-E5A7-4DAE-9F83-6E506605567D%7D&PType_3=%7B54EF6C90-A1A5-47CA-8E49-C5C64D4C82E8%7D")
Can this help a bit? It's only for old version of Xserver.

---

