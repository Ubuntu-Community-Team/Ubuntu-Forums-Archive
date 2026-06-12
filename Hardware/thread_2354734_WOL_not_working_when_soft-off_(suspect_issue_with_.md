---
title: "WOL not working when soft-off (suspect issue with DTDS)"
date: 2017-03-05
forum: Hardware
---

### Post by LastStarDust on 2017-03-05
Hello
I am trying to make wake-on-lan work for my HTPC (FM2A88X-ITX+ motherboard) .
I am almost there since the wol is working when the pc is suspended. But when in the soft-off state the network integrated chip is powered off and can't receive wol packets anymore.
I suspect the issue is related with the DSDT table that is missing the network card reference. I have disabled network manager just in case with the command:
```
echo "manual" | sudo tee /etc/init/network-manager.override
```
Anyways here it is all the information that I could gather:

Network chip info:
```
sudo lshw -C network
[sudo] password for niobe: 
  *-network               
       description: Ethernet interface
       product: QCA8171 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 10
       serial: d0:50:99:35:8b:c8
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx duplex=full ip=192.168.1.207 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:34 memory:fea00000-fea3ffff ioport:e000(size=128)

```

The wol is enabled in the card settings
```
sudo ethtool enp2s0
Settings for enp2s0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supported pause frame use: Symmetric Receive-only
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: Symmetric
    Advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown
    Supports Wake-on: pg
    Wake-on: pg
    Current message level: 0x000060e4 (24804)
                   link ifup rx_err tx_err hw wol
    Link detected: yes

```

DTDS as seen by acpitool
```
acpitool -w
   Device    S-state      Status   Sysfs node
  ---------------------------------------
  1. PB2      S4    *disabled
  2. PB3      S4    *disabled
  3. PB4      S4    *disabled
  4. PB5      S4    *disabled
  5. PB6      S4    *disabled
  6. PB7      S4    *disabled
  7. SBAZ      S4    *disabled  pci:0000:00:14.2
  8. ECIR      S4    *disabled
  9. PS2K      S4    *enabled   pnp:00:07
  10. PS2M      S4    *disabled
  11. P0PC      S4    *disabled  pci:0000:00:14.4
  12. OHC1      S4    *enabled   pci:0000:00:12.0
  13. EHC1      S4    *enabled   pci:0000:00:12.2
  14. OHC2      S4    *enabled   pci:0000:00:13.0
  15. EHC2      S4    *enabled   pci:0000:00:13.2
  16. OHC3      S4    *disabled
  17. EHC3      S4    *disabled
  18. OHC4      S4    *enabled   pci:0000:00:14.5
  19. XHC0      S4    *enabled   pci:0000:00:10.0
  20. XHC1      S4    *enabled   pci:0000:00:10.1
  21. PE20      S4    *disabled  pci:0000:00:15.0
  22. PE21      S4    *disabled
  23. PE22      S4    *disabled
  24. PE23      S4    *disabled

```
note that there is no reference to pci:0000:02:00.0 (the network chip)

These are the Errors and Warings thrown by the dtds compiler
```
dsdt.dsl    142:         If (CondRefOf (_OSI, Local0))
Warning  3144 -                                   ^ Method Local is set but never used (Local0)

dsdt.dsl    217:     Method (MCTH, 2, NotSerialized)
Remark   2120 -                ^ Control Method should be made Serialized (due to creation of named objects within)

dsdt.dsl    604:     Method (GHPS, 2, NotSerialized)
Remark   2146 -                ^ Method Argument is never used (Arg1)

dsdt.dsl    692:     Method (SWAK, 1, NotSerialized)
Remark   2146 -                ^ Method Argument is never used (Arg0)

dsdt.dsl    725:     Method (TRMD, 1, NotSerialized)
Remark   2146 -                ^ Method Argument is never used (Arg0)

dsdt.dsl    838:         If (CondRefOf (_OSI, Local0))
Warning  3144 -                                   ^ Method Local is set but never used (Local0)

dsdt.dsl   2352:                     0xFDFC0000,         // Length
Error    6049 -                              ^ Length is larger than Min/Max window

dsdt.dsl   2359:                     0xFDFC0000,         // Length
Error    6049 -                              ^ Length is larger than Min/Max window

dsdt.dsl   2492:                         CreateDWordField (CRS1, \_SB.PCI0._Y06._MIN, MN8L)  // _MIN: Minimum Base Address
Warning  3128 -                                     ResourceTag larger than Field ^  (Size mismatch, Tag: 64 bits, Field: 32 bits)

dsdt.dsl   2497:                         CreateDWordField (CRS1, \_SB.PCI0._Y06._MAX, MX8L)  // _MAX: Maximum Base Address
Warning  3128 -                                     ResourceTag larger than Field ^  (Size mismatch, Tag: 64 bits, Field: 32 bits)

dsdt.dsl   2500:                         CreateDWordField (CRS1, \_SB.PCI0._Y06._LEN, LN8L)  // _LEN: Length
Warning  3128 -                                     ResourceTag larger than Field ^  (Size mismatch, Tag: 64 bits, Field: 32 bits)

dsdt.dsl   2562:                         CreateDWordField (CRS2, \_SB.PCI0._Y0D._MIN, MN9L)  // _MIN: Minimum Base Address
Warning  3128 -                                     ResourceTag larger than Field ^  (Size mismatch, Tag: 64 bits, Field: 32 bits)

dsdt.dsl   2565:                         CreateDWordField (CRS2, \_SB.PCI0._Y0D._MAX, MX9L)  // _MAX: Maximum Base Address
Warning  3128 -                                     ResourceTag larger than Field ^  (Size mismatch, Tag: 64 bits, Field: 32 bits)

dsdt.dsl   2568:                         CreateDWordField (CRS2, \_SB.PCI0._Y0D._LEN, LN9L)  // _LEN: Length
Warning  3128 -                                     ResourceTag larger than Field ^  (Size mismatch, Tag: 64 bits, Field: 32 bits)

dsdt.dsl   2818:                 Method (GPTS, 1, NotSerialized)
Remark   2146 -                            ^ Method Argument is never used (Arg0)

dsdt.dsl   2822:                 Method (GWAK, 1, NotSerialized)
Remark   2146 -                            ^ Method Argument is never used (Arg0)

dsdt.dsl   3005:                             Divide ((Arg0 * 0xFF), 0x64, Local1, Local0)
Warning  3144 -                            Method Local is set but never used ^  (Local1)

dsdt.dsl   3239:                                 Divide ((Arg0 * 0xFF), 0x64, Local1, Local0)
Warning  3144 -                                Method Local is set but never used ^  (Local1)

dsdt.dsl   3513:                                 Divide ((Arg0 * 0xFF), 0x64, Local1, Local0)
Warning  3144 -                                Method Local is set but never used ^  (Local1)

dsdt.dsl   3709:                 Method (GTM, 1, NotSerialized)
Remark   2120 -                           ^ Control Method should be made Serialized (due to creation of named objects within)

dsdt.dsl   3760:                 Method (STM, 3, NotSerialized)
Remark   2146 -                           ^ Method Argument is never used (Arg1)

dsdt.dsl   3760:                 Method (STM, 3, NotSerialized)
Remark   2146 -                           ^ Method Argument is never used (Arg2)

dsdt.dsl   3760:                 Method (STM, 3, NotSerialized)
Remark   2120 -                           ^ Control Method should be made Serialized (due to creation of named objects within)

dsdt.dsl   3814:                 Method (GTF, 2, NotSerialized)
Remark   2120 -                           ^ Control Method should be made Serialized (due to creation of named objects within)

dsdt.dsl   3870:                     Method (_GTM, 0, NotSerialized)  // _GTM: Get Timing Mode
Remark   2120 -                                ^ Control Method should be made Serialized (due to creation of named objects within)

dsdt.dsl   3889:                     Method (_STM, 3, NotSerialized)  // _STM: Set Timing Mode
Remark   2120 -                                ^ Control Method should be made Serialized (due to creation of named objects within)

dsdt.dsl   3911:                         Method (_GTF, 0, NotSerialized)  // _GTF: Get Task File
Remark   2120 -                                    ^ Control Method should be made Serialized (due to creation of named objects within)

dsdt.dsl   3932:                         Method (_GTF, 0, NotSerialized)  // _GTF: Get Task File
Remark   2120 -                                    ^ Control Method should be made Serialized (due to creation of named objects within)

dsdt.dsl   3954:                     Method (_GTM, 0, NotSerialized)  // _GTM: Get Timing Mode
Remark   2120 -                                ^ Control Method should be made Serialized (due to creation of named objects within)

dsdt.dsl   3973:                     Method (_STM, 3, NotSerialized)  // _STM: Set Timing Mode
Remark   2120 -                                ^ Control Method should be made Serialized (due to creation of named objects within)

dsdt.dsl   3995:                         Method (_GTF, 0, NotSerialized)  // _GTF: Get Task File
Remark   2120 -                                    ^ Control Method should be made Serialized (due to creation of named objects within)

dsdt.dsl   4016:                         Method (_GTF, 0, NotSerialized)  // _GTF: Get Task File
Remark   2120 -                                    ^ Control Method should be made Serialized (due to creation of named objects within)

dsdt.dsl   4067:                 Method (SPTS, 1, NotSerialized)
Remark   2146 -                            ^ Method Argument is never used (Arg0)

dsdt.dsl   4071:                 Method (SWAK, 1, NotSerialized)
Remark   2146 -                            ^ Method Argument is never used (Arg0)

dsdt.dsl   4367:                                     SMB0 = SMB0 /* \_SB_.PCI0.S900._CRS.SMB0 */
Warning  3023 -                Duplicate value in list ^  (Source is the same as Target)

dsdt.dsl   4435:                         IO (Decode16,
Error    6090 -                                    ^ Min/Max/Length/Gran are all zero, but no resource tag

dsdt.dsl   4494:                         Acquire (MUT0, 0x0FFF)
Warning  3130 -                                             ^ Result is not used, possible operator timeout will be missed

dsdt.dsl   4835:                 Method (SIOS, 1, NotSerialized)
Remark   2120 -                            ^ Control Method should be made Serialized (due to creation of named objects within)

dsdt.dsl   4902:                 Method (SIOW, 1, NotSerialized)
Remark   2146 -                            ^ Method Argument is never used (Arg0)

dsdt.dsl   5116:                         Acquire (ECMU, 0x5000)
Warning  3130 -                                             ^ Result is not used, possible operator timeout will be missed

dsdt.dsl   5725:                     Method (_PS0, 0, NotSerialized)  // _PS0: Power State 0
Remark   2120 -                                ^ Control Method should be made Serialized (due to creation of named objects within)

dsdt.dsl   5787:                         Method (_STA, 0, NotSerialized)  // _STA: Status
Remark   2120 -                                    ^ Control Method should be made Serialized (due to creation of named objects within)

dsdt.dsl   5809:                         Method (_PS0, 0, NotSerialized)  // _PS0: Power State 0
Remark   2120 -                                    ^ Control Method should be made Serialized (due to creation of named objects within)

dsdt.dsl   5843:                         Method (_STA, 0, NotSerialized)  // _STA: Status
Remark   2120 -                                    ^ Control Method should be made Serialized (due to creation of named objects within)

dsdt.dsl   5865:                         Method (_PS0, 0, NotSerialized)  // _PS0: Power State 0
Remark   2120 -                                    ^ Control Method should be made Serialized (due to creation of named objects within)

dsdt.dsl   5924:                     Method (_PS0, 0, NotSerialized)  // _PS0: Power State 0
Remark   2120 -                                ^ Control Method should be made Serialized (due to creation of named objects within)

dsdt.dsl   5985:                         Method (_STA, 0, NotSerialized)  // _STA: Status
Remark   2120 -                                    ^ Control Method should be made Serialized (due to creation of named objects within)

dsdt.dsl   6007:                         Method (_PS0, 0, NotSerialized)  // _PS0: Power State 0
Remark   2120 -                                    ^ Control Method should be made Serialized (due to creation of named objects within)

dsdt.dsl   6041:                         Method (_STA, 0, NotSerialized)  // _STA: Status
Remark   2120 -                                    ^ Control Method should be made Serialized (due to creation of named objects within)

dsdt.dsl   6063:                         Method (_PS0, 0, NotSerialized)  // _PS0: Power State 0
Remark   2120 -                                    ^ Control Method should be made Serialized (due to creation of named objects within)

dsdt.dsl   6286:             Local1 = PD64 /* \_SB_.PD64 */
Warning  3144 -                  ^ Method Local is set but never used (Local1)

dsdt.dsl   6557:                 CreateWordField (Arg0, One, IRA)
Remark   2089 -                      Object is not referenced ^  (Name is within method [_SRS])

dsdt.dsl   6701:         Method (_OSC, 4, NotSerialized)  // _OSC: Operating System Capabilities
Remark   2120 -                    ^ Control Method should be made Serialized (due to creation of named objects within)

dsdt.dsl   6714:                     (CTRL & 0x1E)
Error    6114 -                           ^ Result is not used, operator has no effect

dsdt.dsl   6801:                 Method (RRIO, 4, NotSerialized)
Remark   2146 -                            ^ Method Argument is never used (Arg0)

dsdt.dsl   6801:                 Method (RRIO, 4, NotSerialized)
Remark   2146 -                            ^ Method Argument is never used (Arg1)

dsdt.dsl   6801:                 Method (RRIO, 4, NotSerialized)
Remark   2146 -                            ^ Method Argument is never used (Arg2)

dsdt.dsl   6801:                 Method (RRIO, 4, NotSerialized)
Remark   2146 -                            ^ Method Argument is never used (Arg3)

dsdt.dsl   6806:                 Method (RDMA, 3, NotSerialized)
Remark   2146 -                            ^ Method Argument is never used (Arg0)

dsdt.dsl   6806:                 Method (RDMA, 3, NotSerialized)
Remark   2146 -                            ^ Method Argument is never used (Arg1)

dsdt.dsl   6806:                 Method (RDMA, 3, NotSerialized)
Remark   2146 -                            ^ Method Argument is never used (Arg2)

dsdt.dsl   7096:         Method (_HID, 0, NotSerialized)  // _HID: Hardware ID
Warning  3115 -                    ^ Not all control paths return a value (_HID)

dsdt.dsl   7096:         Method (_HID, 0, NotSerialized)  // _HID: Hardware ID
Warning  3107 -                    ^ Reserved method must return a value (Integer/String required for _HID)

dsdt.dsl   7154:         Method (_DSM, 4, NotSerialized)  // _DSM: Device-Specific Method
Remark   2120 -                    ^ Control Method should be made Serialized (due to creation of named objects within)

dsdt.dsl   7158:                 Name (_T_0, Zero)  // _T_x: Emitted by ASL Compiler
Remark   2011 -                          ^ Use of compiler reserved name (_T_0)

dsdt.dsl   7312:                 Name (_T_1, Zero)  // _T_x: Emitted by ASL Compiler
Remark   2011 -                          ^ Use of compiler reserved name (_T_1)

```

Lastly the dmesg lines with errors
```
dmesg | grep Error
[    3.045542] ACPI Error: [\_SB_.ALIB] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
[    3.045548] ACPI Error: Method parse/execution failed [\_SB.PCI0.VGA.ATC0] (Node ffff8802270bf7d0), AE_NOT_FOUND (20150930/psparse-542)
[    3.045554] ACPI Error: Method parse/execution failed [\_SB.PCI0.VGA.ATCS] (Node ffff8802270bf7a8), AE_NOT_FOUND (20150930/psparse-542)

```

Here you can find the [dmesg]("https://drive.google.com/open?id=0B0VJUB4eOu4LUHg2a0xGdVNvek0") output and the [dsdt.dsl]("https://drive.google.com/open?id=0B0VJUB4eOu4LWkFwS0RiMGhqb1U") files

---

