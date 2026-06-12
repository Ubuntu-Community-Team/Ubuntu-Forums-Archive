---
title: "Problems accesing a 8GB Microdrive through a PCMCIA microdrive adapter"
date: 2010-10-21
forum: Hardware
---

### Post by wakaru00 on 2010-10-21
I've recently purchased a few 2nd hand 8GB microdrives from eBay like the one pictured.

[IMG]http://www.hjreggel.de/hdtechdat/ST68022_t.jpg[/IMG]

As far as I know they come from old IPods. I am certain they are in good working order, but whenever I try accessing them via a PCMCIA  microdrive adapter, it won't work.

If I do dmesg, I get the following error:

```

[  132.824051] pcmcia_socket pcmcia_socket0: pccard: PCMCIA card inserted into slot 0
[  132.824488] pcmcia 0.0: pcmcia: registering new device pcmcia0.0
[  132.868841] scsi3 : pata_pcmcia
[  132.868917] ata4: PATA max PIO0 cmd 0x4040 ctl 0x404e irq 3
[  133.048647] ata4.00: CFA: ST68022CF, 3.01, max PIO4
[  133.048652] ata4.00: 15625008 sectors, multi 0: LBA 
[  134.196075] ata4.00: both IDENTIFYs aborted, assuming NODEV
[  134.196080] ata4.00: revalidation failed (errno=-2)
[  138.188232] ata4.00: both IDENTIFYs aborted, assuming NODEV
[  138.188237] ata4.00: revalidation failed (errno=-2)
[  143.344232] ata4.00: both IDENTIFYs aborted, assuming NODEV
[  143.344237] ata4.00: revalidation failed (errno=-2)
[  143.344242] ata4.00: disabled

```I get exactly the same with every Microdrive... 

On the other hand, if I use the same adapter with a IOmega 340MB Microdrive, the device is identified and mounted properly:
[IMG]http://static.howstuffworks.com/gif/removable-storage-microdrive.jpg[/IMG]
```

[ 1075.964053] pcmcia_socket pcmcia_socket0: pccard: PCMCIA card inserted into slot 0
[ 1075.964488] pcmcia 0.0: pcmcia: registering new device pcmcia0.0
[ 1076.007806] scsi4 : pata_pcmcia
[ 1076.007883] ata5: PATA max PIO0 cmd 0x4040 ctl 0x404e irq 3
[ 1077.628089] ata5.01: both IDENTIFYs aborted, assuming NODEV
[ 1077.636663] ata5.00: CFA: IBM-DMDM-10340, MD2IC601, max PIO1
[ 1077.636668] ata5.00: 700560 sectors, multi 0: LBA 
[ 1077.668774] ata5.00: configured for PIO0
[ 1077.668829] isa bounce pool size: 16 pages
[ 1077.668932] scsi 4:0:0:0: Direct-Access     ATA      IBM-DMDM-10340   MD2I PQ: 0 ANSI: 5
[ 1077.669117] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 1077.669164] sd 4:0:0:0: [sdb] 700560 512-byte logical blocks: (358 MB/342 MiB)
[ 1077.669223] sd 4:0:0:0: [sdb] Write Protect is off
[ 1077.669226] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[ 1077.669256] sd 4:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 1077.669442]  sdb: sdb1
[ 1077.713638] sd 4:0:0:0: [sdb] Attached SCSI removable disk

```Could anyone point out to the problem and how to overcome it? Thanks very much in advance

---

### Post by P4man on 2010-10-21
Googling on the error message, I find some posts and reports where people solve similar issues (with internal drives) by booting the kernel with 

```
all_generic_ide
```

Though it appears to slow down those machines considerably, perhaps its worth trying.

---

### Post by wakaru00 on 2010-10-22
Thanks P4man;
 
Your answer make some sense. I will try that suggestion when I get home and report my findings :)
 
I've done some research and according to [Wikipedia ]("http://en.wikipedia.org/wiki/Microdrive")it seems all that these microdrives stripped from devices like the iPods are physically set by their firmware to ATA mode only, hence they will work in IDE mode as they have had their CF/II interface disabled in the firmware.
 
There is also some interesting information concerning the re-use of microdrives in true IDE mode [HERE]("http://www.gearhack.com/Forums/DisplayComments.php?file=Computer/My_Adventure_with_the_Seagate_5_GB_ST1_Drive_.FW._3.08.")

---

### Post by Fafler on 2010-10-22
I can confirm this. I have a 4 gb iPod drive with the same issues. It works in a old USB 1.1 cardreader, everywhere else it fails with the same error, or due to other USB cardreaders supplying 3.3v instead of 5v.

---

### Post by wakaru00 on 2010-10-22
@ Fafler
Are you suggesting this is a voltage issue then? 
Because if it is there is not much I can do about it :(
 
On a second thought it may not be a voltage issue. Whenever I insert the microdrive+PCMCIA adapter into the laptop, I can clearly hear the inners of the microdrive spinning, so I imagine sufficient voltage is coming through.

---

### Post by Ftmmsch on 2012-02-07
> **wakaru00 said:**
> @ Fafler
Are you suggesting this is a voltage issue then? 
Because if it is there is not much I can do about it :(
 
On a second thought it may not be a voltage issue. Whenever I insert the microdrive+PCMCIA adapter into the laptop, I can clearly hear the inners of the microdrive spinning, so I imagine sufficient voltage is coming through.
 
 
 
 
hi
 
are you maybe interested in original packed / sealed:
 
Toshiba
[FONT=Georgia][SIZE=6][COLOR=#4d4d4d][FONT=Georgia][SIZE=6][COLOR=#4d4d4d][FONT=Georgia][SIZE=6][COLOR=#4d4d4d][LEFT][SIZE=2]PCMCIA Type II, 5GB Capacity, PC Card / 68-pin ATA,[/SIZE]
[SIZE=2]Dual Voltage 5V and 3.3V, 300,000 Hours MTTF.[/SIZE][/LEFT]
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Georgia][SIZE=1][COLOR=#4d4d4d][FONT=Georgia][SIZE=1][COLOR=#4d4d4d][FONT=Georgia][SIZE=1][COLOR=#4d4d4d] 
???
 
They are new - sealed   rsp. original packed.
 
If you are interested - send me a mail
 
 
P.S.  i have a few original sealed and packed (which means = not opend / not used)
           and a few, which are opend but original packed.[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

---

