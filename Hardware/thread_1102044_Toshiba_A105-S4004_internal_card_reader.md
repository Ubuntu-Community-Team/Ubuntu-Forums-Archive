---
title: "Toshiba A105-S4004 internal card reader"
date: 2009-03-21
forum: Hardware
---

### Post by lordyoyo on 2009-03-21
I have installed Ubuntu 8.10 on a Toshiba A105-S4004 model, and I'm wondering if I can make the internal card reader work, and if yes, how? Right now I haven't got the slightest clue how to reach it...

---

### Post by camel1cz on 2009-03-21
Hi,

first of all you need to identify your card reader. The lspci and/or lsusb can do the job.

For me lspci gives:
```

# lspci
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

```

and lspci -n
```

03:01.1 0805: 1180:0822 (rev 22)
03:01.2 0880: 1180:0843 (rev 12)
03:01.3 0880: 1180:0592 (rev 12)
03:01.4 0880: 1180:0852 (rev ff)

```

Look for the device ID - number in for XXXX:XXXX - for me it's 1180:0822.
Then you can try serching the net for support - query like 'linux "XXXX:XXXX" support' can be a good start.

Hope it will help.

---

### Post by lordyoyo on 2009-07-29
thx, i found it, did a search on support without any luck. But in 9.04 it has been solved anyways :)

---

