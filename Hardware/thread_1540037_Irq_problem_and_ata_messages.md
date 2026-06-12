---
title: "Irq problem and ata messages"
date: 2010-07-27
forum: Hardware
---

### Post by jejeman on 2010-07-27
Hello everyone,
sometimes I get this messages

> [ 2488.979360] irq 18: nobody cared (try booting with the "irqpoll" option)
[ 2488.979366] Pid: 0, comm: swapper Not tainted 2.6.32-24-generic #38-Ubuntu
[ 2488.979368] Call Trace:
[ 2488.979370]  <IRQ>  [<ffffffff810c6f6b>] __report_bad_irq+0x2b/0xa0
[ 2488.979381]  [<ffffffff810c716c>] note_interrupt+0x18c/0x1d0
[ 2488.979384]  [<ffffffff810c786d>] handle_fasteoi_irq+0xdd/0x100
[ 2488.979389]  [<ffffffff81015d12>] handle_irq+0x22/0x30
[ 2488.979393]  [<ffffffff8154948c>] do_IRQ+0x6c/0xf0
[ 2488.979396]  [<ffffffff81013b13>] ret_from_intr+0x0/0x11
[ 2488.979397]  <EOI>  [<ffffffff8101b5a1>] ? mwait_idle+0x71/0xd0
[ 2488.979404]  [<ffffffff8154711a>] ? atomic_notifier_call_chain+0x1a/0x20
[ 2488.979408]  [<ffffffff81011e73>] ? cpu_idle+0xb3/0x110
[ 2488.979411]  [<ffffffff8153e1fe>] ? start_secondary+0xa8/0xaa
[ 2488.979413] handlers:
[ 2488.979415] [<ffffffff813b5dc0>] (ata_sff_interrupt+0x0/0x120)
[ 2488.979420] [<ffffffff813d57d0>] (usb_hcd_irq+0x0/0x90)
[ 2488.979425] Disabling IRQ #18

after that dvd is not working, it can't mount any disk

```
cat /proc/interrupts
           CPU0       CPU1       
 18:      38339     270494   IO-APIC-fasteoi   ata_piix, uhci_hcd:usb4
```

Also, I get this messages, (not connected to the first one with irq)

> ata1.01: qc timeout (cmd 0xa0)
ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
sr 0:0:1:0: CDB: Test Unit Ready: 00 00 00 00 00 00
ata1.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
         res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
ata1.01: status: { DRDY ERR }
ata1: link is slow to respond, please be patient (ready=0)
ata1: device not ready (errno=-16), forcing hardreset
ata1: soft resetting link
ata1.00: configured for UDMA/66
ata1.01: configured for UDMA/66
ata1: EH complete

they are repeated alot, while computer is working. I can't see that it causes any performance issues.
I've noticed these messages appearing alot to many users. Until Lucid I never noticed them before.

I'm looking for info and solutions regarding these messages.
My system is ubuntu 10.04 64bit
motherboard ASUSTeK Computer INC. Product Name: P5KPL-AM
Intel(R) Core(TM)2 Duo CPU E8400 @ 3.00GHz
PIONEER DVD-RW  DVR-112D
ATA Disk WDC WD3200AAKS-0  (sata ii)

---

### Post by P4man on 2010-07-27
the first line of your first dump suggests a solution; try booting with irqpoll. If you dont know how, look here:

[https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation](https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation)

follow that only replace the VGA=771 with irqpoll.

If it helps; scroll down to see how to make the change permanent.

Another thing you can try is update your bios and play with AHCI settings in the bios.

---

### Post by jejeman on 2010-08-01
After enabling irgpool option in kernel command line, I didn't got irq error messages anymore. But these ata errors keep on showing. 
I realized that this ata errors were afecting the dvd-roms performans. They didn't worked at all. So I tried the following:

1. disconected both dvd devices. - no more ata errors
2. removed irqpool option from kernel line - no more irq errors
3. connected just one dvd device - no more ata errors or irq errors

Conclusion:
Irq and ata errors were related. The irq was assinged to ata controler, and it got errors which were made by attached dvd devices. For some reason the 2 dvd devices setup was giving errors to the system. After disconecting one dvd device (wich I realy don't need) everything is working normal.

The suggestion for irqpool kernel command, worked but I think it gave some other misc. errors. The main problem was in hardware setup and had to be resolved on that level. Okay, maybe the linux kenrel had problem with this current setup, and some other not, but I can't prove that.

Thanks for reply.

---

