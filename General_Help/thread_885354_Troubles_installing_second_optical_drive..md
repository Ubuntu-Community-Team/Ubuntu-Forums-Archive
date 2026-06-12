---
title: "Troubles installing second optical drive."
date: 2008-08-10
forum: General Help
---

### Post by LordLandon on 2008-08-10
I'm running hardy-server, which originally had one cd drive. I've added a second optical drive, a DVD burner, and am now having odd issues.

Things that work:
/dev/scd0 and /dev/scd1 both exist, and are ejectable.
wodim dev=/dev/scd0 <somefile> and wodim dev=/dev/scd1 <somefile> both seem to work.
So I know the physical connections are fine.

Things that don't:
the disks wodim burns don't seem to be readable, but, I'm likely using the tool wrong.
nautalius and brasero both segfault when there are disks in the drives.
nautalius seems to no longer be able to access computer:/// with the error message "Nautilus cannot handle computer: locations."

I can't seem to find a verbose switch for nautalius, but -g with brasero didn't seem to be of much help to me.


Any help would be appreciated (=

---

### Post by cariboo on 2008-08-10
Have you tried any other burning program, such as gnomebaker or k3b?
You might want to try loading a genreic kernel at boot time just to see if it makes a difference.

Jim

---

### Post by LordLandon on 2008-08-10
gnomebaker has also segfaulted, and I am running the standard kernel.

)=

---

### Post by mc4man on 2008-08-10
> added a second optical drive, a DVD burner, and am now having odd issues.You haven't mentioned how and where the new drive is installed. Assuming 2 ide optical drives, are they on the same cable and if so what position is the new drive. Also what type of cable - 40 or 80 wire, is the new drive on? (on a 40 wire the wires are obvious

If it's on a 40 wire I'd look at the things below

Take a look at what's shown for udma on the new drive (scd1?) Should at least show udma2 being set, is it udma4 capable?

> sudo hdparm -i /dev/scdx

also maybe look in your various logs for DMA and UDMA or grep some logs for both before and after inserting cd
ex.
grep 'UDMA' /var/log/kern.log
grep 'DMA' /var/log/kern.log
and the same in dmesg

---

### Post by LordLandon on 2008-08-11
> **mc4man said:**
> You haven't mentioned how and where the new drive is installed. Assuming 2 ide optical drives, are they on the same cable and if so what position is the new drive.,/QUOTE]
Yes, two IDE drives, same cable. Old one Master, new one Slave
> 
Also what type of cable - 40 or 80 wire, is the new drive on? (on a 40 wire the wires are obvious

If it's on a 40 wire I'd look at the things below

Take a look at what's shown for udma on the new drive (scd1?) Should at least show udma2 being set, is it udma4 capable?
I'm not sure as to how to tell the difference between 40 wire and 80 wire, but here's what I get from hdparm: 
```

$ sudo hdparm -i /dev/scd0
[sudo] password for lordlandon: 

/dev/scd0:

 Model=LITE-ON COMBO LTC-48161H                , FwRev=KH0P    , SerialNo=                    
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:227,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 udma3 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-5

 * signifies the current active mode

$ sudo hdparm -i /dev/scd1

/dev/scd1:

 Model=PIONEER DVD-RW  DVR-109                 , FwRev=1.50    , SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=13395, BuffSize=64kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 udma3 udma4 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-2,3,4,5

 * signifies the current active mode


```
[QUOTE]
also maybe look in your various logs for DMA and UDMA or grep some logs for both before and after inserting cd
ex.
grep 'UDMA' /var/log/kern.log
grep 'DMA' /var/log/kern.log
and the same in dmesg

```

$ grep 'UDMA' /var/log/kern.log | tail -n 10
Aug 10 00:34:23 MooSE kernel: [   25.581227] ata1.00: ATA-7: SAMSUNG SP0802N, TK100-24, max UDMA/100
Aug 10 00:34:23 MooSE kernel: [   25.630441] ata1.01: ATA-7: ST3250620A, 3.AAD, max UDMA/100
Aug 10 00:34:23 MooSE kernel: [   25.641142] ata1.00: configured for UDMA/100
Aug 10 00:34:23 MooSE kernel: [   25.713440] ata1.01: configured for UDMA/100
Aug 10 00:34:23 MooSE kernel: [   26.210468] ata2.00: ATAPI: LITE-ON COMBO LTC-48161H, KH0P, max UDMA/44
Aug 10 00:34:23 MooSE kernel: [   26.210489] ata2.01: ATAPI: PIONEER DVD-RW  DVR-109, 1.50, max UDMA/66
Aug 10 00:34:23 MooSE kernel: [   26.210501] ata2.00: limited to UDMA/33 due to 40-wire cable
Aug 10 00:34:23 MooSE kernel: [   26.210504] ata2.01: limited to UDMA/33 due to 40-wire cable
Aug 10 00:34:23 MooSE kernel: [   26.370275] ata2.00: configured for UDMA/33
Aug 10 00:34:23 MooSE kernel: [   26.570048] ata2.01: configured for UDMA/33


$ grep 'DMA' /var/log/kern.log | tail -n 10
Aug 10 00:34:23 MooSE kernel: [   26.210468] ata2.00: ATAPI: LITE-ON COMBO LTC-48161H, KH0P, max UDMA/44
Aug 10 00:34:23 MooSE kernel: [   26.210489] ata2.01: ATAPI: PIONEER DVD-RW  DVR-109, 1.50, max UDMA/66
Aug 10 00:34:23 MooSE kernel: [   26.210501] ata2.00: limited to UDMA/33 due to 40-wire cable
Aug 10 00:34:23 MooSE kernel: [   26.210504] ata2.01: limited to UDMA/33 due to 40-wire cable
Aug 10 00:34:23 MooSE kernel: [   26.370275] ata2.00: configured for UDMA/33
Aug 10 00:34:23 MooSE kernel: [   26.570048] ata2.01: configured for UDMA/33
Aug 10 00:34:23 MooSE kernel: [   34.108522] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Aug 10 00:55:16 MooSE kernel: [ 1294.419847] cdrom: sr0: mrw address space DMA selected
Aug 10 00:56:51 MooSE kernel: [ 1389.004531] cdrom: sr0: mrw address space DMA selected
Aug 10 00:56:51 MooSE kernel: [ 1389.113485] cdrom: sr0: mrw address space DMA selected

```

and some relevant-looking lines from dmesg:
```

[88502.844356] cdrom: This disc doesn't have any tracks I recognize!
[88505.084430] printk: 4 messages suppressed.
[88505.084438] nautilus[8806]: segfault at 00000000 eip 00000000 esp b69c925c error 4

```

---

### Post by mc4man on 2008-08-11
As far as the logs there's nothing outstanding other than the nautilus segfault.
The line about 'limited to UDMA/33 due to 40-wire cable' may or may not be a factor. Many UDMA/66 (udma4) drives cannot be set to that in linux even if on an 80 wire cable. In those cases they'll be set to UDMA/33 and you'll get that line even when actually on an 80 wire.
I have a liteon that shows that and works perfectly, the performance difference between udma2 and udma4 is minimal.

In any event you should be using an 80 wire for those drives. On the 40 wire you can clearly see the wires, the 80 is somewhat smooth. Your hdd's would be on an 80 wire, compare the 2.

While it may not be the source of your issues i'd put the pioneer burner on the end connector(mastered) of your secondary ide and the cd/combo drive as slave. (and ck. the jumpers, cable type)

If you do that (switch positions), before making the switch I'd go to   /etc/udev/rules.d/70-persistent-cd.rules and delete all the entries, shut down, make the switch and reboot. (the entries will be properly recreated on boot) Leave it looking as such
```
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
```

note: if this error was found in dmesg then it would be of concern
> Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)


---

### Post by LordLandon on 2008-08-23
I found an 80 wire cable, and put the drives on that instead (turns out I was using 40 wire; didn't even know the difference until this thread). It seems fine now ^.^

Thanks for your help, guys.

---

### Post by LordLandon on 2008-08-23
Hmm, spoke too soon...

Segfaults again, even if there's just the DVD burner connected, and properly set to master...

---

