---
title: "irda problem with IBM T40p"
date: 2005-04-19
forum: Hardware &amp; Laptops
---

### Post by warp on 2005-04-19
my problem is with irda sync of my pda and my notebook... 

i got palm m505 and IBM notebook T40p

i cant connect to the palm, i've tested if the irda transmitter is working at all, and in w1ndoze XP it works... pity i use them only for gaming ;D

before i had an older palm, so i used crandle and gpilotd deamon to sync with evolution... 

i got these loaded modules 
warp@warp:/$ lsmod | grep ir
firmware_class          9728  1 ipw2100
irtty_sir               7936  0
sir_dev                18092  1 irtty_sir
irda                  168000  2 irtty_sir,sir_dev
crc_ccitt               2176  1 irda

also my dmesg gives me this
root@warp:~# dmesg | grep ir
** workaround, the "pci=routeirq" argument restores the old
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
ICH4: not 100% native mode: will probe irqs later
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
ide1 at 0x170-0x177,0x376 on irq 15
EXT3-fs: INFO: recovery required on readonly filesystem.
 Firmware: 5.9
parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
irda_init()
uhci_hcd 0000:00:1d.0: irq 11, io base 0x1800
uhci_hcd 0000:00:1d.1: irq 11, io base 0x1820
uhci_hcd 0000:00:1d.2: irq 11, io base 0x1840
ehci_hcd 0000:00:1d.7: irq 11, pci mem 0xc0000000
Yenta: ISA IRQ mask 0x0438, PCI irq 11
Yenta: ISA IRQ mask 0x0438, PCI irq 11
ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, 1.0.2
ipw2100: Detected Intel PRO/Wireless 2100 Network Connection


my /proc/net/irda info is this
root@warp:/proc/net# ls irda -la
total 0
dr-xr-xr-x  2 root root 0 2005-04-19 19:32 .
dr-xr-xr-x  6 root root 0 2005-04-19 14:54 ..
-r--r--r--  1 root root 0 2005-04-19 19:32 discovery
-r--r--r--  1 root root 0 2005-04-19 19:32 irias
-r--r--r--  1 root root 0 2005-04-19 19:32 irlap
-r--r--r--  1 root root 0 2005-04-19 19:32 irlmp
-r--r--r--  1 root root 0 2005-04-19 19:32 irttp

i wonder why are all these files of zero size... 

i have read about 40 howtos, i spend this whole day sorting this out... nothing helped, i tried also
dpkg-reconfigure irda-utils 
and set them to SIR and none FIR chip... so i tried to find the FIR chipset... which should be there, because in windoze it works at 4mbps

my findchip comman return this

root@warp:/proc/net# findchip -d -v
Probing for FDC37C669 ...
Wrong chip id=0xff
Wrong chip id=0xff
Probing for FDC37C669FR ...
Wrong chip id=0xff
Wrong chip id=0xff
Probing for FDC37N869 ...
Wrong chip id=0xff
Wrong chip id=0xff
Probing for FDC37C93xFR ...
Wrong chip id=0xff
Wrong chip id=0xff
Probing for FDC37N957FR ...
Wrong chip id=0xff
Wrong chip id=0xff
Probing for FDC37N958FR ...
Wrong chip id=0xff
Wrong chip id=0xff
Probing for PC87108 ...
no chip at 0x150
no chip at 0x398
no chip at 0x0ea
Probing for PC87338 ...
no chip at 0x398
no chip at 0x15c
Wrong chip id=0x00
Probing for EFER at 0x03f0 ...
hefras = 0xff
Probing for EFER at 0x0370 ...
hefras = 0xff
EFER seems to be probed at 0x0370
chip id = 0xff, revision = 0xff
Wrong device ID = 0xff
Probing for EFER at 0x0250 ...
hefras = 0xff
Probing for EFER at 0x0250 ...
hefras = 0xff
Probing for EFER at 0x03f0 ...
hefras = 0xff
hefere = 0xff
Probing for EFER at 0x03f0 ...
hefras = 0xff
hefere = 0xff
EFER seems to be probed at 0x03f0
chip ID is 0x0f : no known chip was detected.
Couldn't find Winbond superI/O chip.



so it didn't found any know chip, so i suppose i have to use the SIR serial... 

but i tried everything i know to make it, i wonder why irdadump returns nothing... 

PLEASE PLEASE PLEASE HELP ME WITH THIS...

---

### Post by ayk on 2005-05-22
Same problem, i have a Sharp GX25 and the Irda doesn't work, although the IBM chipset seems to work with Linux ([http://irda.sourceforge.net/chipsets.html](http://irda.sourceforge.net/chipsets.html) )... 

Any help would be thankful...

---

