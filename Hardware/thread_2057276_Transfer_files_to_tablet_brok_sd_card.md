---
title: "Transfer files to tablet brok sd card"
date: 2012-09-13
forum: Hardware
---

### Post by rpdayton on 2012-09-13
I have ubuntu 12.04 on my desktop.
I plugged in my tablet (pandigital) to the usb to put music files on it, onto the memory card (32 gb pny microsd)
The files (50 files) began copying fine, but after about 50% it got slower and slower and slower, then finely stopped and ubuntu gave an error that the microsd card could not be found.
after a few seconds, it opened up like I had just plugged it in, only now i cant copy files to it because it says it is "read only".
I did a 'safely remove', and restarted my tablet, but now it says the card is not mounted or has no files.
I put the card into the card reader on my desktop, and ubuntu finds it, with all the files, but wont let me copy any files to it because it is 'read only'.
I put the card in my windows laptop, and it also says it is read only.
 
fsck dosfsck, chown, and remounting the drive all fail because "read-only file system."
 
Windows chkdsk finds nothing wrong, but cannot do a "automatically fix file system errors" because it is a "read only file system".
 
I see a lot of mentions online that complain about ubuntu making read-only file systems on memory cards, and i see a lot of mentions about file transfers in ubuntu getting slower and slower.
 
is this something that can be fixed or do i need to loose all my data and start all over, and why does ubuntu have a big problem causing this?

---

### Post by rpdayton on 2012-09-13
ok I took a 16gb pny card that was in my music player and i put it in the tablet and formated it with android.  it was a good memory card and it was used for allmost a year with no troubles.  if this works then it was a bad 32gb pny card.
i copied lots of files from the tablet's internal memory onto the sd card and it copied them just fine.
so then i copied 1 or 2 pictures from my ubuntu desktop computer and it copied them just fine using nautilus and drag and drop method.
then i copied a few songs about 2 or 3 and they copied fine.
then i tried to copy 10 songs at once and it copied the first ones ok then it got slower and slower and finely after about 5 minutes it said there was an error copying because it couldnt find the memory stick anymore.
so then i turned off the tablet and put in the memory stick to the card reader and yep it is read only now.
my windows laptop also said it is read only
so i erased it formatted it in windows on my laptop and then i copied files from windows to it almost 4 gb and no problem and very fast.
so i put it into the tablet and it can see all the files and i copy them from the card to the internal memory with no problem.
then i put the card in my ubuntu 12.04 desktop and after copyed 6 songs, about 56 mb, it slowed down and finely said it cant find the device then it was read only again.
i started my desktop with the live dvd and tried it from there and yep.  same thing, still made it read only.
so now i took my 32gb card and reformated it and in windows it works just fine and in the tablet it works just fine but i want to know: how can i copy files from ubuntu to the card without making read only?

---

### Post by rpdayton on 2012-09-14
ok so I had an idea to download a brand new live disk of ubuntu 12.04 and boot my laptop to ubuntu.
and just to make sure, i bought a new memory card (8gb).
and so I used windows chkdsk to make sure the card was good, and no errors found.
and then i used windows to copy "my documents" (about 200 files) and it only took a minute to copy with no problem.
then i erased them and ran chkdsk again, and no problem.
so the card is good right?
then I booted my laptop to the ubuntu live disk and tried to copy the same files from windows documents to the card and it copied and copied and copied and got slower and slower and finely it gave an error that it couldnt find the card anymore.
then i rebooted my laptop to windows (xp) and ran a chkdsk and ut oh its read only.
and i put it in my tablet and it cant mount it.
 
in conclusion: the only thing that makes my cards read only is ubuntu and on 2 different machines all together.  so anyway with so many people online talking about how slow it is to copy files in ubuntu and lot's of people saying they got a read only file system from ubuntu then what is the way to fix it?

---

### Post by rpdayton on 2012-09-14
If no body know`s how to fix this then maybe I should file a bug report, but I don't know how too do that, could somebody please help me?

---

### Post by Kulix on 2012-09-24
I have been having a similar problem after I tried to transfer files to my Samsung tablet three weeks ago. I got rid of my tablet after frustrations with that issue only to find out that now all external media(SD and Flash drives) tell me that they are read only when in Ubuntu.
     In windows these work just fine. I can move files from the SD or flash to my computer, but but I can not delete or put files on any of these drives always getting a read only error message.
       Previous to today, when I would try to move files to the external media I was getting a error saying that there was no such file on my external media which is ridiculous because I was trying to move the file from my computer to my SD in the first place. 
       After this I decided to experiment by reformatting my SD card since the filesystem check came back as not clean. I got this error
 " Error creating filesystem
An error occurred while performing an operation on "510 MB filesystem" (Partition 1 of Generic Multi Card): the operation failed
Details: Error creating file system: helper exited with exit code 1: cannot open /dev/sdb1: Read only file system
       From this point on when I try to move files to my sd I get "Error while copying to"ED****" the destination is read only.

And then I also have this problem which started in the last week where the my computer will connect to any wifi network and cable internet but it wont actually let me on the internet](*,)All in all Im going crazy

---

### Post by rpdayton on 2012-11-18
OK so I filed a bug report on launchpad witch I think is the right place to file bugs because google says that's where all the ubuntu 12.04 bugs go.  Anyway, I asked and asked if I did it right, because I don't really know what all to attach, and no body here ever helped me at all except Kulix who is having exactly the same problem (like ALOT of people
But i never heard any thing there either.
So now i have been useing Ubuntu 12.10 Quantum Quetzle and here's what happened with that.
first off, they made it so I can't make videos full screen any more, but only on the internet.  Why would some body write a program to do that? I don't know. It's stupid.
then, they made it so I can't run "system log" either.  It use to be a program that would show a record of all the things Ubuntu 12.04 was doing when you started it or when it was running.  It was really nice but I guess they got rid of it or something.
But here's the really stupid part.  I bought a new media player at best buy for 20$ because I didn't want to take chances with my good one.  Good thing too, because even in Ubuntu 12.10 it is still making a read only file system when I copy lot's of files and not just songs either.
So they didn't fix it even though they knew about it because I filed a bug report about it in plenty of time to have it so it stopped making music players read only.  And since this player was only a player with no SD memory it ended up making the whole thing useless so I took it back to best buy and told them what happened and they didn't want to give me back my money because they said I should only use windows which they tried to sell me because they said Ubuntu isn't really a good operating system with so many people having problems with not just media players but alot of other things too.
So now I can't use ubuntu 12.10 to copy music to a player without breaking it and alot of other people can't too, and with all the other things that they made worse with 12.10 it just seems like they don't care if people have problems or not so I don't guess I understand what ubuntu is thinking anymore.
And since other people have the same problems then is there any way for somebody else to fix it?  I heard that it is possible for any one to fix bugs in ubuntu and maybe there is a way to hire a professional programmer to figure it out?  I mean as much money as I have spent in memory cards and I'm sure other people too then maybe we could pay to have someone else look at it and figure out how to get rid of the part that makes it change things to read only because that really seems like it doesn't do any good for any reason at all.

---

### Post by efflandt on 2012-11-18
This is not a general problem with 12.04.  I boot both 64-bit Lubuntu and Ubuntu 12.04 (with common /home partition) from 32 GB SDHC card on a tablet PC with internally USB connected card slot (Acer W500P).  I never had any trouble originally writing the operating system to the SD card or from files I wrote to that or another 16 GB SD card for 11.10 from the USB card reader my 12.04 desktop (including entire minecraft client and server directories) to both cards.

So there must be something specific about the USB hardware or connection method that results in the slowdown and eventual read-only.  For example is the card reader directly connected to USB, short cable like 6" (15 cm) or less, or a long cable (how long)?  And if [micro]SDHC what class card? A higher class like Class 10 may require more power than Class 4, although, any USB port (other than possibly on laptop or smaller) should provide 500 mA @ 5 VDC.  Maybe that drops off on a battery powered computer device during extended use.

Maybe someone could find common ground on the issue from the output of **lspci** and **lsusb** or it might require digging deeper into the output of **sudo lspci -v**, **sudo lsusb -v**, and **sudo lshw**.

Just letting you know that it is not a general problem that most of us have not experienced.  The only time I had microSD end up as read-only was when a tight slot on a card reader kept tripping the loose Lock switch on microSD to SD adapter.

---

### Post by rpdayton on 2012-11-19
ok.  so I don't have time to search for all the posts about read only file systems but it was not just me, there are a lot of other people who have the same thing and also with it getting slower and slower.
before, i tried useing the cp command because there were some posts that said that will make copying quicker, and that post was a couple years old!  but even with the cp command i will still get a read only file system.
I have 2 card readers on my desktop, one is with a maybe 2' feet cable, and the other is built in straight to the motherboard.
The laptop i don't know, it is built into the side, but it works fine with windows, it only makes read only when i boot to a ubuntu disk so.....
I don't know what classes all of my microsd cards are, is there some way to check?  and I don't know what class the media player was either.  it was a gpx brand but didnt have a memory slot or anything, if that helps.
and I don't know how to find out ma's or any of those things?
and now i can do a lspci and lsusb and lshw after work tonight, do you think that will help?
should i do it right after it makes it read only?

---

### Post by rpdayton on 2012-11-21
ok.

lspci
00:00.0 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: NVIDIA Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: NVIDIA Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB controller: NVIDIA Corporation MCP61 USB 1.1 Controller (rev a3)
00:02.1 USB controller: NVIDIA Corporation MCP61 USB 2.0 Controller (rev a3)
00:04.0 PCI bridge: NVIDIA Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: NVIDIA Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: NVIDIA Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: NVIDIA Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
02:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 440] (rev a1)
02:00.1 Audio device: NVIDIA Corporation GF108 High Definition Audio Controller (rev a1)


lsusb
Bus 001 Device 003: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 002 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



sudo lspci -v
00:00.0 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a1)
	Subsystem: Biostar Microtech Int'l Corp Device 3407
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: [44] HyperTransport: Slave or Primary Interface
	Capabilities: [dc] HyperTransport: MSI Mapping Enable+ Fixed-

00:01.0 ISA bridge: NVIDIA Corporation MCP61 LPC Bridge (rev a2)
	Subsystem: Biostar Microtech Int'l Corp Device 3407
	Flags: bus master, 66MHz, fast devsel, latency 0
	I/O ports at 4f00 [size=256]

00:01.1 SMBus: NVIDIA Corporation MCP61 SMBus (rev a2)
	Subsystem: Biostar Microtech Int'l Corp Device 3407
	Flags: 66MHz, fast devsel, IRQ 11
	I/O ports at 4900 [size=64]
	I/O ports at 4d00 [size=64]
	I/O ports at 4e00 [size=64]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:01.2 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a2)
	Subsystem: Biostar Microtech Int'l Corp Device 3407
	Flags: 66MHz, fast devsel

00:02.0 USB controller: NVIDIA Corporation MCP61 USB 1.1 Controller (rev a3) (prog-if 10 [OHCI])
	Subsystem: Biostar Microtech Int'l Corp Device 3407
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at deeff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: ohci_hcd

00:02.1 USB controller: NVIDIA Corporation MCP61 USB 2.0 Controller (rev a3) (prog-if 20 [EHCI])
	Subsystem: Biostar Microtech Int'l Corp Device 3407
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at deefec00 (32-bit, non-prefetchable) [size=256]
	Capabilities: [44] Debug port: BAR=1 offset=0098
	Capabilities: [80] Power Management version 2
	Kernel driver in use: ehci_hcd

00:04.0 PCI bridge: NVIDIA Corporation MCP61 PCI bridge (rev a1) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	Capabilities: [b8] Subsystem: NVIDIA Corporation Device cb84
	Capabilities: [8c] HyperTransport: MSI Mapping Enable- Fixed-

00:05.0 Audio device: NVIDIA Corporation MCP61 High Definition Audio (rev a2)
	Subsystem: Biostar Microtech Int'l Corp Device 821f
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at deef8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
	Capabilities: [50] MSI: Enable- Count=1/1 Maskable+ 64bit+
	Capabilities: [6c] HyperTransport: MSI Mapping Enable- Fixed+
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

00:06.0 IDE interface: NVIDIA Corporation MCP61 IDE (rev a2) (prog-if 8a [Master SecP PriP])
	Subsystem: Biostar Microtech Int'l Corp Device 3407
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	I/O ports at ffa0 [size=16]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: pata_amd
	Kernel modules: pata_amd

00:07.0 Bridge: NVIDIA Corporation MCP61 Ethernet (rev a2)
	Subsystem: Biostar Microtech Int'l Corp Device 3407
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 43
	Memory at deefd000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at d080 [size=8]
	Capabilities: [44] Power Management version 2
	Capabilities: [50] MSI: Enable+ Count=1/8 Maskable+ 64bit+
	Capabilities: [6c] HyperTransport: MSI Mapping Enable- Fixed+
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:08.0 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: Biostar Microtech Int'l Corp Device 5405
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	I/O ports at d000 [size=8]
	I/O ports at cc00 [size=4]
	I/O ports at c880 [size=8]
	I/O ports at c800 [size=4]
	I/O ports at c480 [size=16]
	Memory at deefc000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Capabilities: [b0] MSI: Enable- Count=1/4 Maskable- 64bit+
	Capabilities: [cc] HyperTransport: MSI Mapping Enable- Fixed+
	Kernel driver in use: sata_nv
	Kernel modules: sata_nv

00:08.1 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: Biostar Microtech Int'l Corp Device 5405
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	I/O ports at c400 [size=8]
	I/O ports at c080 [size=4]
	I/O ports at c000 [size=8]
	I/O ports at bc00 [size=4]
	I/O ports at b880 [size=16]
	Memory at deef7000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Capabilities: [b0] MSI: Enable- Count=1/4 Maskable- 64bit+
	Capabilities: [cc] HyperTransport: MSI Mapping Enable- Fixed+
	Kernel driver in use: sata_nv
	Kernel modules: sata_nv

00:09.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: def00000-dfffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000ddffffff
	Capabilities: [40] Subsystem: Biostar Microtech Int'l Corp Device 3407
	Capabilities: [48] Power Management version 2
	Capabilities: [50] MSI: Enable+ Count=1/2 Maskable- 64bit+
	Capabilities: [60] HyperTransport: MSI Mapping Enable- Fixed-
	Capabilities: [80] Express Root Port (Slot+), MSI 00
	Capabilities: [100] Virtual Channel
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:0b.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Capabilities: [40] Subsystem: Biostar Microtech Int'l Corp Device 3407
	Capabilities: [48] Power Management version 2
	Capabilities: [50] MSI: Enable+ Count=1/2 Maskable- 64bit+
	Capabilities: [60] HyperTransport: MSI Mapping Enable- Fixed-
	Capabilities: [80] Express Root Port (Slot+), MSI 00
	Capabilities: [100] Virtual Channel
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:0c.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Capabilities: [40] Subsystem: Biostar Microtech Int'l Corp Device 3407
	Capabilities: [48] Power Management version 2
	Capabilities: [50] MSI: Enable+ Count=1/2 Maskable- 64bit+
	Capabilities: [60] HyperTransport: MSI Mapping Enable- Fixed-
	Capabilities: [80] Express Root Port (Slot+), MSI 00
	Capabilities: [100] Virtual Channel
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
	Flags: fast devsel
	Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
	Flags: fast devsel
	Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
	Flags: fast devsel
	Capabilities: [f0] Secure device <?>
	Kernel driver in use: k10temp
	Kernel modules: k10temp

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
	Flags: fast devsel

02:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 440] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: eVga.com. Corp. Device 1441
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at df000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=128M]
	Memory at dc000000 (64-bit, prefetchable) [size=32M]
	I/O ports at ec00 [size=128]
	[virtual] Expansion ROM at def80000 [disabled] [size=512K]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [78] Express Endpoint, MSI 00
	Capabilities: [b4] Vendor Specific Information: Len=14 <?>
	Capabilities: [100] Virtual Channel
	Capabilities: [128] Power Budgeting <?>
	Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
	Kernel driver in use: nvidia
	Kernel modules: nvidia_current, nouveau, nvidiafb

02:00.1 Audio device: NVIDIA Corporation GF108 High Definition Audio Controller (rev a1)
	Subsystem: eVga.com. Corp. Device 1441
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at def7c000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [78] Express Endpoint, MSI 00
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel


sudo lsusb -v
Bus 001 Device 003: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x058f Alcor Micro Corp.
  idProduct          0x6366 Multi Flash Reader
  bcdDevice            1.00
  iManufacturer           1 Generic
  iProduct                2 Mass Storage Device
  iSerial                 3 058F63666471
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
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
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk-Only
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
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
Device Status:     0x0000
  (Bus Powered)

Bus 002 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x046d Logitech, Inc.
  idProduct          0xc52b Unifying Receiver
  bcdDevice           12.01
  iManufacturer           1 Logitech
  iProduct                2 USB Receiver
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           84
    bNumInterfaces          3
    bConfigurationValue     1
    iConfiguration          4 RQR12.01_B0019
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               98mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      1 Keyboard
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      59
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               8
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     148
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               2
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      98
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               2
Device Status:     0x0000
  (Bus Powered)

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            3.05
  iManufacturer           3 Linux 3.5.0-18-generic ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:02.1
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
  bLength              11
  bDescriptorType      41
  nNbrPorts            10
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00 0x00
  PortPwrCtrlMask    0xff 0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
   Port 7: 0000.0503 highspeed power enable connect
   Port 8: 0000.0100 power
   Port 9: 0000.0100 power
   Port 10: 0000.0100 power
Device Status:     0x0001
  Self Powered

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            3.05
  iManufacturer           3 Linux 3.5.0-18-generic ohci_hcd
  iProduct                2 OHCI Host Controller
  iSerial                 1 0000:00:02.0
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
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength              11
  bDescriptorType      41
  nNbrPorts            10
  wHubCharacteristic 0x0012
    No power switching (usb 1.0)
    No overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00 0x00
  PortPwrCtrlMask    0xff 0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0103 power enable connect
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
   Port 7: 0000.0100 power
   Port 8: 0000.0100 power
   Port 9: 0000.0100 power
   Port 10: 0000.0100 power
Device Status:     0x0001
  Self Powered

---

