---
title: "Hangs on logout/shutdown, prints error messages"
date: 2016-02-09
forum: Hardware
---

### Post by corbin.loftis on 2016-02-09
Hi everyone. I hope someone can help me. I just got a new desktop (Asus M32), and installed Ubuntu MATE 14.04 on it. Every time I have logged out or shut down, it prints the error messages below that I got through grep. I do have my drive encrypted and home encrypted, and I happen to also be experiencing an as-yet unsolved audio problem. If anyone can help, it would be greatly appreciated.

```
[  562.112222] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.112224] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.112257] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.112264] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.112266] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.112268] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.112686] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.112698] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.112716] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.112718] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.112742] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.112749] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.112751] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.112753] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.112811] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.112818] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.112820] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.112822] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.113076] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.113083] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.113085] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.113087] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.113173] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.113180] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.113182] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.113184] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.113194] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.113214] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.113221] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.113223] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.113225] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.113479] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.113486] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.113488] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.113490] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.113576] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.113583] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.113585] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.113587] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.113620] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.113627] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.113629] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.113631] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.114032] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.114044] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.114061] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.114063] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.114105] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.114112] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.114114] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.114116] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.114518] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.114544] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.114546] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.114548] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.114930] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.114942] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.114959] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.114960] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.114970] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.114991] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.114997] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.115000] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.115001] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.115371] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.115383] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.115400] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.115402] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.115612] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.115633] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.115647] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.115660] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.115963] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.115974] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.115978] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.115982] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.116600] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.116618] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.116623] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.116626] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.116635] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.116649] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.116667] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.116671] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.116675] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.116690] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.116706] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.116753] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.116764] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.116768] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.116772] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.116830] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.116841] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.116845] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.116849] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.116918] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.116936] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.116940] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.116944] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.116953] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.116997] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.117008] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.117012] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.117016] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.117419] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.117430] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.117434] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.117445] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.117453] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.117553] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.117564] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.117569] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.117573] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.117993] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.118004] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.118008] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.118012] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.118379] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.118390] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.118394] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.118398] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.119260] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.119271] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.119276] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.119280] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.119377] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.119387] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.119392] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.119396] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.119474] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.119485] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.119499] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.119503] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.121304] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.121326] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.121332] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.121337] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.121346] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.121361] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.121375] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.121389] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.121403] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.121416] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.121430] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.121448] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.121453] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.121457] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.121466] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.121491] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.121502] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.121507] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.121510] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.121577] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.121588] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.121593] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.121597] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.122180] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.122192] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.122197] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.122201] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.122210] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.122224] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.122238] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.122439] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.122451] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.122455] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.122459] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.122894] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.122905] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.122909] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.122913] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.123281] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.123292] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.123296] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.123300] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.123840] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.123857] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.123864] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.123869] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.124305] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.124317] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.124329] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.124334] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.124343] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.124680] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.124691] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.124695] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.124700] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.124708] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.124937] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.124949] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.124953] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.124957] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.125079] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.125090] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.125094] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.125098] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.125167] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.125178] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.125182] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.125186] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.125403] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.125414] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.125419] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.125423] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.125491] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.125503] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.125507] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.125511] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.125535] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.125546] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.125551] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.125555] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.125651] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.125662] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.125667] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.125670] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.125695] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.125706] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.125711] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.125715] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.125844] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.125855] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.125859] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.125863] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.126433] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.126444] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.126448] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.126452] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.126514] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.126525] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.126529] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.126533] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.126558] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.126576] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.126581] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.126584] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.126593] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.127075] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.127086] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.127090] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.127094] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.127103] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.127135] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.127146] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.127151] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.127155] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.127193] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.127204] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.127209] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.127213] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.127237] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.127255] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.127260] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.127264] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.127272] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.127474] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.127485] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.127489] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.127493] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.127572] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.127590] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.127602] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.127620] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.127641] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.127669] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.127698] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.128133] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.128143] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.128146] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.128150] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.128370] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.128380] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.128384] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.128387] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.128457] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.128467] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.128470] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.128474] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.129114] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.129125] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.129128] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.129132] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.129252] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.129262] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.129265] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.129269] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.129373] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.129389] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.129393] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.129396] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.129404] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.129419] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.129423] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.129426] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.129433] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.129556] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.129566] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.129570] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.129573] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.129593] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.129603] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.129606] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.129609] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.129654] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.129663] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.129667] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.129670] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.130024] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.130034] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.130037] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.130040] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.130068] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.130077] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.130081] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.130084] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.130154] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.130164] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.130167] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.130171] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.130658] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.130667] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.130671] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.130674] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.130702] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.130711] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.130715] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.130718] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.131080] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.131089] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.131093] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.131096] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.131231] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.131240] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.131244] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.131247] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.131274] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.131284] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.131288] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.131291] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.131525] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.131534] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.131538] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.131541] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.131570] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
[  562.131587] pcieport 0000:00:1c.6: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e6(Receiver ID)
[  562.131598] pcieport 0000:00:1c.6:   device [8086:a116] error status/mask=00000001/00002000
[  562.131613] pcieport 0000:00:1c.6:    [ 0] Receiver Error        
[  562.131628] pcieport 0000:00:1c.6: AER: Corrected error received: id=00e6
```

I am currently trying to fix my audio problem as well, and will search and post separately.

Thank you.

---

### Post by corbin.loftis on 2016-02-09
Does anyone know what this error could be caused by?

EDIT (2016-02-09 @ 20:14): 

When I went into bios and turned off Azalia HD Audio, restarted and then shutdown again, it did not display this; but, then my audio controls did not show any audio cards (only 'dummy audio') and alsamixer would not load. Upon re-enabling, my audio card shows up again and alsamixer loads, but still no audio, and I have not seen if it shows the code again, but it probably does...

---

### Post by corbin.loftis on 2016-02-12
I have not heard back from anyone... I reinstalled 14.04 and it does the same thing, only it scrolls more slowly through the error messages now. I am upgrading to 15.10 right now to see if it is a problem between the older software and the newer hardware.

---

### Post by seiye on 2016-02-25
I have the exact same problem and error messages as above.  The kern.log and sys.log fills up my hard-drive, 100GB each after a few hours.  Any updates?

> **corbin.loftis said:**
> I have not heard back from anyone... I reinstalled 14.04 and it does the same thing, only it scrolls more slowly through the error messages now. I am upgrading to 15.10 right now to see if it is a problem between the older software and the newer hardware.

---

### Post by seiye on 2016-02-25
> **seiye said:**
> I have the exact same problem and error messages as above.  The kern.log and sys.log fills up my hard-drive, 100GB each after a few hours.  Any updates?

The excess error messages went away after I disabled RealTek LAN controller in BIOS.  This is a Asus M32 desktop btw running on Ubuntu 14.04

---

### Post by tynaarlo on 2016-03-14
I had the same problem with my Asus M32CD with a Nvidia GTX 960 graphic card. Then I found the solution right [here]("http://ubuntuforums.org/showthread.php?t=2312977&p=13437616#post13437616").
Set the following GRUB options:
```
pci=nomsi
i915.preliminary_hw_support=1
```

I left the CSM option in UEFI on auto. I just had to change the Secure Boot Control to "Other OS".

Edit: I tried without the i915 option and it's still working. I guess the i915 option is for Intel graphic cards only.

---

