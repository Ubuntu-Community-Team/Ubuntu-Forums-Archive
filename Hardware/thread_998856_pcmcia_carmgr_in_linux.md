---
title: "pcmcia carmgr in linux?"
date: 2008-12-01
forum: Hardware
---

### Post by maestrobwh1 on 2008-12-01
Using 8.10 Kubuntu.

I rarely if ever need to use a pcmcia card... and when I did it was a network card and just worked when inserted.

I have a pcmcia card reader that used to lock up the boot, but now in Intrepid, the card doesn't lock up the computer.  It seems to be detected.

If I do lspcmcia, I get
Socket 0 Bridge:        [yenta_cardbus]         (bus ID: 0000:00:06.0)
Socket 0 Device 0:      [pata_pcmcia]           (bus ID: 0.0)

And that is the result with a 1GB SD card inserted.

In the hal device manager, it is also listed under PCI1410 pc card Cardbus Controller as

Memory Card Adapter II
-->SCSI Host Adapter.

So the card is being detected, but not necessarily the SD card inserted into it.  A "sudo blkid" also confirms that the volume is not detected.

I tried some old standard commands I thought would work with pcmciautils and pcmcia-cs installed.

cardmgr and cardinfo return "command not found"

I think the card works, but I don't know how to "use" it under Linux?

---

