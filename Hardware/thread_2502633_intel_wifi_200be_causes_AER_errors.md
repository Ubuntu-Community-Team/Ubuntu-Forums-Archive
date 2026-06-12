---
title: "intel wifi 200be causes AER errors"
date: 2024-11-22
forum: Hardware
---

### Post by brcisna-u on 2024-11-22
New wifi network card into pc 

lspci
```
03:00.0 Network controller: Intel Corporation Wi-Fi 7(802.11be) AX1775*/AX1790*/BE20*/BE401/BE1750* 2x2 (rev 1a)


```

causes constant AER errors in syslog

```
207.321461] pcieport 0000:00:1c.7: AER: Correctable error message received from 0000:00:1c.7Nov 22 13:40:27 server2 kernel: [  207.321467] pcieport 0000:00:1c.7: PCIe Bus Error: severity=Correctable, type=Physical Layer, (Receiver ID)
Nov 22 13:40:27 server2 kernel: [  207.321469] pcieport 0000:00:1c.7:   device [8086:a397] error status/mask=00000001/00002000
Nov 22 13:40:27 server2 kernel: [  207.321470] pcieport 0000:00:1c.7:    [ 0] RxErr                  (First)
Nov 22 13:40:27 server2 kernel: [  207.323973] pcieport 0000:00:1c.7: AER: Correctable error message received from 0000:00:1c.7
Nov 22 13:40:27 server2 kernel: [  207.323979] pcieport 0000:00:1c.7: PCIe Bus Error: severity=Correctable, type=Physical Layer, (Receiver ID)
Nov 22 13:40:27 server2 kernel: [  207.323980] pcieport 0000:00:1c.7:   device [8086:a397] error status/mask=00000001/00002000
Nov 22 13:40:27 server2 kernel: [  207.323982] pcieport 0000:00:1c.7:    [ 0] RxErr                  (First)
Nov 22 13:40:27 server2 kernel: [  207.324715] pcieport 0000:00:1c.7: AER: Correctable error message received from 0000:00:1c.7
Nov 22 13:40:27 server2 kernel: [  207.324719] pcieport 0000:00:1c.7: PCIe Bus Error: severity=Correctable, type=Physical Layer, (Receiver ID)
Nov 22 13:40:27 server2 kernel: [  207.324720] pcieport 0000:00:1c.7:   device [8086:a397] error status/mask=00000001/00002000
Nov 22 13:40:27 server2 kernel: [  207.324721] pcieport 0000:00:1c.7:    [ 0] RxErr                  (First)
Nov 22 13:40:27 server2 kernel: [  207.326766] pcieport 0000:00:1c.7: AER: Correctable error message received from 0000:00:1c.7
Nov 22 13:40:27 server2 kernel: [  207.326773] pcieport 0000:00:1c.7: PCIe Bus Error: severity=Correctable, type=Physical Layer, (Receiver ID)
Nov 22 13:40:27 server2 kernel: [  207.326774] pcieport 0000:00:1c.7:   device [8086:a397] error status/mask=00000001/00002000
Nov 22 13:40:27 server2 kernel: [  207.326776] pcieport 0000:00:1c.7:    [ 0] RxErr                  (First)
Nov 22 13:40:27 server2 kernel: [  207.327466] pcieport 0000:00:1c.7: AER: Correctable error message received from 0000:00:1c.7
Nov 22 13:40:27 server2 kernel: [  207.327472] pcieport 0000:00:1c.7: PCIe Bus Error: severity=Correctable, type=Physical Layer, (Receiver ID)
Nov 22 13:40:27 server2 kernel: [  207.327473] pcieport 0000:00:1c.7:   device [8086:a397] error status/mask=00000001/00002000
Nov 22 13:40:27 server2 kernel: [  207.327474] pcieport 0000:00:1c.7:    [ 0] RxErr                  (First)
```

updated BIOS,,,disabled ASPM in bios to disable power management

if i do this edit at boot time these AER errors are gone
[COLOR=#0C0D0E][FONT=-apple-system]pci=noaer 


kernel
[/FONT][/COLOR]```
Linux server2 6.11.5+bpo-amd64 #1 SMP PREEMPT_DYNAMIC Debian 6.11.5-1~bpo12+1 (2024-11-11) x86_64 GNU/Linux


```[COLOR=#0C0D0E][FONT=-apple-system]
Placed into another pcie slot and is the same errors

I think this is in conjunction with possibly iwlwifi firmware,,but can not figure out how to disect it.

Would rather actualyl fix the problem,,than mask the problem by putting the 'pci-noaer' on the kernel commandline

is there such a thing as flashing new firmware into these cheap consumer grade cards.

TIA



[/FONT][/COLOR]

---

