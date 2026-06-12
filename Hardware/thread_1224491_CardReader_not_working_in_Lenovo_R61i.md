---
title: "CardReader not working in Lenovo R61i"
date: 2009-07-27
forum: Hardware
---

### Post by tayran on 2009-07-27
Hi all,

I haven't tried it since i had installed Kubuntu 9.04 to my Lenovo R61i but yesterday i saw that the Ricoh cardreader isn't working.

When i insert a memory card into the reader i see a yellow light flashing but nothing happens.

The result of lsmod is below:

ricoh_mmc               3596  0
output                  2764  1 video
rsrc_nonstatic         11372  1 yenta_socket
pcmcia_core            36480  3 pcmcia,yenta_socket,rsrc_nonstatic

and the result of lshw -c system:

*-system:2 UNCLAIMED
       description: System peripheral
       product: xD-Picture Card Controller
       vendor: Ricoh Co Ltd
       physical id: 0.5
       bus info: pci@0000:15:00.5
       version: 11
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0


and i can see messages about it in logs:

grep "ricoh-mmc" /var/log/messages

Jul 27 13:28:47 bsugur kernel: [    8.197288] ricoh-mmc: Ricoh MMC Controller disabling driver
Jul 27 13:28:47 bsugur kernel: [    8.197291] ricoh-mmc: Copyright(c) Philip Langdale
Jul 27 13:28:47 bsugur kernel: [    8.197326] ricoh-mmc: Ricoh MMC controller found at 0000:15:00.3 [1180:0843] (rev 11)
Jul 27 13:28:47 bsugur kernel: [    8.197358] ricoh-mmc: Controller is now disabled.
Jul 27 18:39:51 bsugur kernel: [14757.918396] ricoh-mmc: Suspending.
Jul 27 18:39:51 bsugur kernel: [14757.918428] ricoh-mmc: Controller is now re-enabled.
Jul 27 18:39:52 bsugur kernel: [14760.552228] ricoh-mmc: Resuming.
Jul 27 18:39:52 bsugur kernel: [14760.552260] ricoh-mmc: Controller is now disabled.


lspci | grep Ricoh
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)

Can you suggest anything?

Thanks...

---

