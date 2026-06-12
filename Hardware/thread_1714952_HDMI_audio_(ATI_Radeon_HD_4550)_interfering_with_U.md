---
title: "HDMI audio (ATI Radeon HD 4550) interfering with USB?"
date: 2011-03-26
forum: Hardware
---

### Post by maestro716 on 2011-03-26
Installed version 10.10 and using open source driver for ATI Radeon HD 4550.  Originally had serious keyboard/mouse lag issues with  fglrx, so switched to the open source driver.  I have no input lag issues now so long as I boot up with the HDMI audio disabled.  The minute I enable HDMI audio output, I have keyboard and mouse lag issues again that won't go away unless I deactivate the HDMI audio and reboot.  It seems that something about activating the HDMI audio is messing with the USB ports.  

Here's my interrupts before activating HDMI:

           CPU0       
  0:         28   IO-APIC-edge      timer
  1:         49   IO-APIC-edge      i8042
  6:          3   IO-APIC-edge      floppy
  7:          1   IO-APIC-edge      parport0
  8:          0   IO-APIC-edge      rtc0
  9:          1   IO-APIC-fasteoi   acpi, firewire_ohci
 12:       2984   IO-APIC-edge      i8042
 14:      11735   IO-APIC-edge      pata_atiixp
 15:      14137   IO-APIC-edge      pata_atiixp
 17:          1   IO-APIC-fasteoi   ATI IXP
 18:      13603   IO-APIC-fasteoi   radeon, hda_intel
 19:     312407   IO-APIC-fasteoi   ehci_hcd:usb1, ohci_hcd:usb2, ohci_hcd:usb3
 20:      12260   IO-APIC-fasteoi   eth0
 22:          0   IO-APIC-fasteoi   sata_sil
 23:          0   IO-APIC-fasteoi   sata_sil
NMI:          0   Non-maskable interrupts
LOC:     594083   Local timer interrupts
SPU:          0   Spurious interrupts
PMI:          0   Performance monitoring interrupts
PND:          0   Performance pending work
RES:          0   Rescheduling interrupts
CAL:          0   Function call interrupts
TLB:          0   TLB shootdowns
TRM:          0   Thermal event interrupts
THR:          0   Threshold APIC interrupts
MCE:          0   Machine check exceptions
MCP:         10   Machine check polls
ERR:          1
MIS:          0

And here's the interrupts immediately after activating the HDMI audio:
           CPU0       
  0:         28   IO-APIC-edge      timer
  1:         54   IO-APIC-edge      i8042
  6:          3   IO-APIC-edge      floppy
  7:          1   IO-APIC-edge      parport0
  8:          0   IO-APIC-edge      rtc0
  9:          1   IO-APIC-fasteoi   acpi, firewire_ohci
 12:       7588   IO-APIC-edge      i8042
 14:      11986   IO-APIC-edge      pata_atiixp
 15:      14527   IO-APIC-edge      pata_atiixp
 17:          1   IO-APIC-fasteoi   ATI IXP
 18:      16181   IO-APIC-fasteoi   radeon, hda_intel
 19:    1000002   IO-APIC-fasteoi   ehci_hcd:usb1, ohci_hcd:usb2, ohci_hcd:usb3
 20:      12294   IO-APIC-fasteoi   eth0
 22:          0   IO-APIC-fasteoi   sata_sil
 23:          0   IO-APIC-fasteoi   sata_sil
NMI:          0   Non-maskable interrupts
LOC:     619071   Local timer interrupts
SPU:          0   Spurious interrupts
PMI:          0   Performance monitoring interrupts
PND:          0   Performance pending work
RES:          0   Rescheduling interrupts
CAL:          0   Function call interrupts
TLB:          0   TLB shootdowns
TRM:          0   Thermal event interrupts
THR:          0   Threshold APIC interrupts
MCE:          0   Machine check exceptions
MCP:         10   Machine check polls
ERR:          1
MIS:          0

And for good measure, here's my lspci and lsusb results:

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:11.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV710 [Radeon HD 4550]
01:00.1 Audio device: ATI Technologies Inc RV710/730
02:01.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)

Bus 003 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 002: ID 0dba:1000  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Interrupts on channel 19 are clearly spiking but I don't know why.  I am a total newbie at this, so any help is greatly appreciated.  Anybody know what I can do to resolve this or investigate further?  Thanks in advance.

---

### Post by maestro716 on 2011-04-06
For anyone who may stumble upon this thread with similar issues...

I discovered that Ubuntu was disabling IRQ 19 during bootup because of some type of IRQ debugging process that occurs by default on startup.  My workaround was to disable the process by inserting a "noirqdebug" boot option.

For those who are newbies like myself, i basically followed these instructions for modifying grub2, but added noirqdebug instead of irqpoll.
[http://woolie.co.uk/technology/usb-devices-not-working-fujitsu-amilo-l7310gw](http://woolie.co.uk/technology/usb-devices-not-working-fujitsu-amilo-l7310gw)

Hope this helps someone!

---

### Post by dave_t on 2013-01-02
Thank you! I was days trying to figure this out. As soon as I inserted "noirqdebug" as a boot option my OS became usable.

---

