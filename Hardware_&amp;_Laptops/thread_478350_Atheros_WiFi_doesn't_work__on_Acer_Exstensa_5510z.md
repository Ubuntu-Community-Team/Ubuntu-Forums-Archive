---
title: "Atheros WiFi doesn't work  on Acer Exstensa 5510z"
date: 2007-06-19
forum: Hardware &amp; Laptops
---

### Post by Dig[]Dug on 2007-06-19
Hi all,

i've recivied a new laptop  for working ,Acer Exstensa 5510z but i can't to work the wifi card ,
Atheros card unknown model .
The following results of lspci -vv command execution :

05:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
        Subsystem: AMBIT Microsystem Corp. Unknown device 0428
        Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 19
        Region 0: Memory at d0000000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [40] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0-,D1-,D2-,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
                Address: 00000000  Data: 0000
        Capabilities: [60] Express Legacy Endpoint IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
                Device: Latency L0s <512ns, L1 <64us
                Device: AtnBtn- AtnInd- PwrInd-
                Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
                Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
                Device: MaxPayload 128 bytes, MaxReadReq 512 bytes
                Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 0
                Link: Latency L0s <512ns, L1 <64us
                Link: ASPM Disabled RCB 128 bytes CommClk- ExtSynch-
                Link: Speed 2.5Gb/s, Width x1
        Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
                Vector table: BAR=0 offset=00000000
                PBA: BAR=0 offset=00000000

At the boot of my laptop ,Linux load the module ath_pci but it doens't work .
I've tried to reload the module by the following command :

rmmod ath_pci
rmmod ath_hal 

dmesg says :

[10130.600000] ath_pci: driver unloaded
[10138.256000] ath_hal: driver unloaded


modprobe ath_pci

dmesg says :

[10223.460000] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 19 (level, low) -> IRQ 19
[10223.460000] PCI: Setting latency timer of device 0000:05:00.0 to 64
[10223.464000] wifi%d: unable to attach hardware: 'Hardware didn't respond as expected' (HAL status 3)
[10223.464000] ACPI: PCI interrupt for device 0000:05:00.0 disabled

tha card can't switch on maybe ....why this message 'Hardware didn't respond as expected' (HAL status 3) ?

Someone can help me to find the solution to get card work ...


Thanks in advance ,

Bye 

Stefano Leandro
*nix SysAdmin

---

### Post by ukripper on 2007-06-19
Post your output for dmesg here:

```
dmesg | grep wifi
```

---

### Post by AlReece45 on 2007-07-19
My friend is having what appears to be the same problem. I can't copy and paste output here, since it currently doesn't have internet. But `dmesg | grep wifi` doesn't output anything until I unload ath_hal and ath_pci and then reload them. When reloading them, I get the same message as above:

```
[10223.464000] wifi%d: unable to attach hardware: 'Hardware didn't respond as expected' (HAL status 3)
```

His laptop is an Acer Aspire 3100

---

### Post by Twintop on 2007-07-19
You both would probably be able to use acer_acpi to get his wifi working -  [http://code.google.com/p/aceracpi/](http://code.google.com/p/aceracpi/) . It works on Aspire 5100s, so 3100s should work as well (they're effectively the same model), and most of the newer Acer laptops in general have the same acpi system. If it does work, please let the project admin know! :)

---

