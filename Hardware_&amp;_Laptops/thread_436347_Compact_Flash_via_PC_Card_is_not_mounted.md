---
title: "Compact Flash via PC Card is not mounted"
date: 2007-05-07
forum: Hardware &amp; Laptops
---

### Post by Schrollini on 2007-05-07
I just bought a SanDisk CompactFlash PC Card Adapter to mount the Compact Flash card from my camera on my laptop.  Unfortunately, when I plug the card in, the laptop beeps and the following message is displayed on all open terminals:

```
Message from syslogd@switters at Tue May  8 00:42:52 2007 ...
switters kernel: [17179761.512000] Disabling IRQ #3
```If I watch dmesg as I plug in the card, these lines appear immediately

```
[17451666.840000] pccard: PCMCIA card inserted into slot 0
[17451666.840000] pcmcia: registering new device pcmcia0.0
[17451666.880000] ata7: PATA max PIO0 cmd 0x100 ctl 0x10E bmdma 0x0 irq 3
[17451667.168000] irq 3: nobody cared (try booting with the "irqpoll" option)
[17451667.168000]  <c01499a4> __report_bad_irq+0x24/0x80  <c0149a9d> note_interrupt+0x9d/0x270
[17451667.168000]  <c0149323> handle_IRQ_event+0x33/0x60  <c0149448> __do_IRQ+0xf8/0x110
[17451667.168000]  <c0105c89> do_IRQ+0x19/0x30  <c010408a> common_interrupt+0x1a/0x20
[17451667.168000]  <c012782f> __do_softirq+0x5f/0xe0  <c01278e5> do_softirq+0x35/0x40
[17451667.168000]  <c0105c8e> do_IRQ+0x1e/0x30  <c010408a> common_interrupt+0x1a/0x20
[17451667.168000]  <c02dad29> _spin_unlock_irqrestore+0x9/0x10  <c0149749> setup_irq+0x99/0x140
[17451667.168000]  <dcd1dfe0> ata_interrupt+0x0/0x140 [libata]  <c0149889> request_irq+0x99/0xb0
[17451667.168000]  <dcd1d61a> ata_device_add+0x3ba/0x630 [libata]  <dcb6956e> pcmcia_init_one+0x49e/0x5d0 [pata_pcmcia]
[17451667.168000]  <dca406dc> pcmcia_device_probe+0x6c/0x120 [pcmcia]  <c0246174> driver_probe_device+0x44/0xc0
[17451667.168000]  <c02d8728> klist_next+0x38/0x60  <c02459f4> bus_for_each_drv+0x44/0x70
[17451667.168000]  <c0246268> device_attach+0x68/0x70  <c02461f0> __device_attach+0x0/0x10
[17451667.168000]  <c02458c8> bus_add_device+0x28/0x110  <c0244a87> device_add+0xf7/0x150
[17451667.168000]  <dca3fe9e> pcmcia_device_add+0x1ae/0x260 [pcmcia]  <dca40012> pcmcia_card_add+0xa2/0xb0 [pcmcia]
[17451667.168000]  <c0122dd8> vprintk+0x298/0x340  <dc99287c> ti12xx_power_hook+0x14c/0x1f0 [yenta_socket]
[17451667.168000]  <dca400a0> ds_event+0x80/0xb0 [pcmcia]  <dc9af371> send_event+0x51/0xb0 [pcmcia_core]
[17451667.168000]  <dc9af820> socket_insert+0x90/0xf0 [pcmcia_core]  <dc9afce4> pccardd+0x234/0x250 [pcmcia_core]
[17451667.168000]  <c011bde0> default_wake_function+0x0/0x10  <dc9afab0> pccardd+0x0/0x250 [pcmcia_core]
[17451667.168000]  <c0101005> kernel_thread_helper+0x5/0x10 
[17451667.168000] handlers:
[17451667.168000] [<dcd1dfe0>] (ata_interrupt+0x0/0x140 [libata])
[17451667.168000] Disabling IRQ #3
```and then, a few seconds later, these lines appear:

```
[17451697.336000] ata7: qc timeout (cmd 0x91)
[17451697.336000] ata7: dev 0 failed to IDENTIFY (INIT_DEV_PARAMS failed)
[17451697.336000] scsi6 : pata_pcmcia
```

If I try booting with the irqpoll option, as dmesg suggests, the computer hangs as soon as I plug in the card.

Does anyone know how to fix this or have suggestions of tricks to try?  I don't really know where to begin when it comes to hardware issues.

If it makes a difference, the Compact Flash card is a Lexar Media 128MB card which is probably five years old by now.  The laptop is a Compaq Presario 2100 running an up-to-date version of Edgy.  (The same thing happens with the Fiesty Live CD.)  lspci gives:
```
00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1
```

Please don't hesitate to ask for more information that might shed some light on this problem.  Thanks!

---

### Post by Schrollini on 2007-05-08
I've poked around and found some more diagnostics, but I don't know what they mean.

cat /proc/interrupts
```
           CPU0       
  0:      89220          XT-PIC  timer
  1:        109          XT-PIC  i8042
  2:          0          XT-PIC  cascade
  3:     100001          XT-PIC  libata
  5:       1334          XT-PIC  ALI 5451
  7:          2          XT-PIC  parport0
  8:          3          XT-PIC  rtc
  9:       5881          XT-PIC  acpi
 10:          0          XT-PIC  ohci_hcd:usb1, radeon@pci:0000:01:05.0
 11:        835          XT-PIC  yenta, eth0
 12:       2845          XT-PIC  i8042
 14:       6794          XT-PIC  ide0
 15:       2678          XT-PIC  ide1
NMI:          0 
LOC:          0 
ERR:          0
MIS:          0

```

It looks like there is something to handle IRQ #3, but for some reason it doesn't.

pccardctl ident
```
Socket 0:
  product info: "CL ATA FLASH CARD LEXAR  ", "TIDALWV", "V100N", ""
  manfid: 0x4e01, 0x0200
  function: 4 (fixed disk)
```

pccardctl status
```
Socket 0:
  3.3V 16-bit PC Card
  Subdevice 0 (function 0) bound to driver "pata_pcmcia"
```

pccardctl ls
```
Socket 0 Bridge:        [yenta_cardbus]         (bus ID: 0000:00:0a.0)
Socket 0 Device 0:      [pata_pcmcia]           (bus ID: 0.0)
```

It looks like the card is being recognized fine, but it never gets made into a block device that can be mounted.  Is there a way I can force that to happen, despite the various errors that occur?

---

### Post by MikeBenza on 2007-06-13
Did you have any luck getting this working?  I'm looking to buy the same PC card, but I don't want to waste my money.

---

### Post by Schrollini on 2007-06-17
> **MikeBenza said:**
> Did you have any luck getting this working?  I'm looking to buy the same PC card, but I don't want to waste my money.

I'm afraid not.  I'm sure it's possible, but I couldn't figure it out, and I got deafening silence here, on the email list, and on IRC.  So I returned the PC card for a USB adapter that has worked with no fuss at all.

I should note that I suspect the problem was with my computer, not the card itself.  Everything I've read suggests that the CompactFlash to PC card connection is trivial.  However, I don't have any other PC cards with which I can test this theory.

---

### Post by Alexander Heß on 2007-08-14
I have a similar problem using a SanDisk 6in1-reader.

Interesting thing is: When booting from the Feisty-livecd the inserted sd-card mounts just fine.

---

### Post by Zta on 2007-08-16
Anyone working on this bug?  I'm experiencing it as well.

---

### Post by dakevman on 2007-08-21
ich have the same problme...

---

