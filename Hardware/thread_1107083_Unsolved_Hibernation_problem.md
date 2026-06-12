---
title: "Unsolved Hibernation problem"
date: 2009-03-26
forum: Hardware
---

### Post by muppetjones on 2009-03-26
Problem: Hibernate does not always work. Half the time I hibernate, it goes to a blank screen with a blinking cursor in the top left hand corner. While I have seen possible solutions to similar problems, nothing has worked. If I close down all programs and hibernate from the shut down menu, it seems to work. If I don't close down programs or if I simply close the lid, I get the frozen screen and the fan stays on.

System: 8.10 with Adam's Kernel on an EEE 1000. 1gb RAM w/ 2gb Swap.

EDIT: I also tested to make sure my swap was working (as this was largely the problem I found online). It is mounted, and with tons of programs up and running I saw 50mb of swap used once ~90-95% of RAM was used.

Thanks in advance for help!

Here is the system log; I'm nearly certain this is from when I tried to hibernate. I got the blank screen, held down the power button to turn off, and a minute or so later, turned it back on.

```

Mar 26 11:27:41 muppetjones-nous kernel: [ 1498.361232] RX DESC f7b46000  size = 2048
Mar 26 11:27:41 muppetjones-nous kernel: [ 1498.361896] <-- RTMPAllocTxRxRingMemory, Status=0
Mar 26 11:27:41 muppetjones-nous kernel: [ 1498.366198] 1. Phy Mode = 0
Mar 26 11:27:41 muppetjones-nous kernel: [ 1498.366212] 2. Phy Mode = 0
Mar 26 11:27:41 muppetjones-nous kernel: [ 1498.395507] 3. Phy Mode = 0
Mar 26 11:27:41 muppetjones-nous kernel: [ 1498.395542] MCS Set = 00 00 00 00 00
Mar 26 11:27:41 muppetjones-nous kernel: [ 1498.401984] <==== RTMPInitialize, Status=0
Mar 26 11:27:41 muppetjones-nous kernel: [ 1498.402063] 0x1300 = 000a4260
Mar 26 11:27:42 muppetjones-nous kernel: [ 1499.313240] RX DESC f368e000  size = 2048
Mar 26 11:27:42 muppetjones-nous kernel: [ 1499.313946] <-- RTMPAllocTxRxRingMemory, Status=0
Mar 26 11:27:42 muppetjones-nous kernel: [ 1499.323780] 1. Phy Mode = 0
Mar 26 11:27:42 muppetjones-nous kernel: [ 1499.323802] 2. Phy Mode = 0
Mar 26 11:27:42 muppetjones-nous kernel: [ 1499.355107] 3. Phy Mode = 0
Mar 26 11:27:42 muppetjones-nous kernel: [ 1499.355132] MCS Set = 00 00 00 00 00
Mar 26 11:27:42 muppetjones-nous kernel: [ 1499.361654] <==== RTMPInitialize, Status=0
Mar 26 11:27:42 muppetjones-nous kernel: [ 1499.361732] 0x1300 = 000a4260
Mar 26 11:29:24 muppetjones-nous syslogd 1.5.0#2ubuntu6: restart.
```

---

