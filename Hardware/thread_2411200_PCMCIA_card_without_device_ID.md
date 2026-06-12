---
title: "PCMCIA card without device ID"
date: 2019-01-26
forum: Hardware
---

### Post by fely35 on 2019-01-26
The pcmcia card that's working with windows 10, does not with Ubuntu 18.04. 
The device ID is not reported. I cannot find out what the problem is.
The system is a DELL Optiplex XE2.


```

~$ pccardctl status
Socket 0:
  5.0V
 16-bit
 PC Card
 
```

```

~$ pccardctl info
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

```


```

00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:16.3 Serial controller: Intel Corporation 8 Series/C220 Series Chipset Family KT Controller (rev 04)
00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I217-LM (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d4)
00:1c.1 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #2 (rev d4)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Q87 Express LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GP107 [GeForce GTX 1050 Ti] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GP107GL High Definition Audio Controller (rev a1)
03:00.0 PCI bridge: Texas Instruments XIO2001 PCI Express-to-PCI Bridge
**04:02.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller**

```

```

~$ cat /proc/interrupts 
           CPU0       CPU1       CPU2       CPU3       
  0:          9          0          0          0  IR-IO-APIC   2-edge      timer
  8:          0          0          1          0  IR-IO-APIC   8-edge      rtc0
  9:          0          4          0          0  IR-IO-APIC   9-fasteoi   acpi
 16:          0          0         29          0  IR-IO-APIC  16-fasteoi   ehci_hcd:usb1
 17:          0          0          0        807  IR-IO-APIC  17-fasteoi   snd_hda_intel:card2
 18:          0          0          0          0  IR-IO-APIC  18-fasteoi   i801_smbus
 **19:         14          1          0          0  IR-IO-APIC  19-fasteoi   yenta**
 23:          0          0          0         33  IR-IO-APIC  23-fasteoi   ehci_hcd:usb2
 24:          0          0          0          0  DMAR-MSI   0-edge      dmar0
 25:          0          0          0          0  DMAR-MSI   1-edge      dmar1
 26:          0          0          0          0  IR-PCI-MSI 16384-edge      PCIe PME
 27:          0          0          0          0  IR-PCI-MSI 458752-edge      PCIe PME
 28:          0          0          0          0  IR-PCI-MSI 460800-edge      PCIe PME
 29:       8268      97332          0      34406  IR-PCI-MSI 327680-edge      xhci_hcd
 30:      56761          0          0          0  IR-PCI-MSI 512000-edge      ahci[0000:00:1f.2]
 31:          0        179          0     162136  IR-PCI-MSI 409600-edge      eno1
 32:          0        650        120          0  IR-PCI-MSI 32768-edge      i915
 33:          0          0          0         31  IR-PCI-MSI 360448-edge      mei_me
 34:          0        601     302098          0  IR-PCI-MSI 524288-edge      nvidia
 35:          0          0        465          0  IR-PCI-MSI 442368-edge      snd_hda_intel:card1
 36:          0          0        224          0  IR-PCI-MSI 49152-edge      snd_hda_intel:card0
NMI:         15         20         16         16   Non-maskable interrupts
LOC:     208702     198795     194977     203980   Local timer interrupts
SPU:          0          0          0          0   Spurious interrupts
PMI:         15         20         16         16   Performance monitoring interrupts
IWI:          0          1          0          0   IRQ work interrupts
RTR:          0          0          0          0   APIC ICR read retries
RES:      36904      31585      30861      24926   Rescheduling interrupts
CAL:      30360      34620      30602      29221   Function call interrupts
TLB:      26197      31958      27457      26297   TLB shootdowns
TRM:          0          0          0          0   Thermal event interrupts
THR:          0          0          0          0   Threshold APIC interrupts
DFR:          0          0          0          0   Deferred Error APIC interrupts
MCE:          0          0          0          0   Machine check exceptions
MCP:          8          9          9          9   Machine check polls
HYP:          0          0          0          0   Hypervisor callback interrupts
ERR:          0
MIS:          0
PIN:          0          0          0          0   Posted-interrupt notification event
NPI:          0          0          0          0   Nested posted-interrupt event
PIW:          0          0          0          0   Posted-interrupt wakeup event

```

DMESG:
[https://paste.ubuntu.com/p/pM9sMPq65N/](https://paste.ubuntu.com/p/pM9sMPq65N/)

---

### Post by fely35 on 2019-01-26
```
[    0.111462] pci 0000:04:02.0: BAR 15: no space for [mem size 0x04000000 pref]
[    0.111463] pci 0000:04:02.0: BAR 15: failed to assign [mem size 0x04000000 pref]
[    0.111465] pci 0000:04:02.0: BAR 16: no space for [mem size 0x04000000]
[    0.111466] pci 0000:04:02.0: BAR 16: failed to assign [mem size 0x04000000]
[    0.111467] pci 0000:04:02.0: BAR 13: assigned [io  0xc000-0xc0ff]
[    0.111468] pci 0000:04:02.0: BAR 14: assigned [io  0xc400-0xc4ff]
[    0.111470] pci 0000:04:02.0: BAR 16: no space for [mem size 0x04000000]
[    0.111471] pci 0000:04:02.0: BAR 16: failed to assign [mem size 0x04000000]
[    0.111473] pci 0000:04:02.0: BAR 15: no space for [mem size 0x04000000 pref]
[    0.111474] pci 0000:04:02.0: BAR 15: failed to assign [mem size 0x04000000 pref]

```

That is the problem.

---

### Post by fely35 on 2019-01-26
Found the solution:

GRUB boot argument:

pci=cbmemsize=8M

was needed.

And sometimes I have to eject and inject the card, if it is not detected.

---

