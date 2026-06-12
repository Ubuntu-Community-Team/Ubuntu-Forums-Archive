---
title: "Mwave modem manager crashes on Thinkpad 600E (Xubuntu 7.04)"
date: 2007-10-13
forum: Hardware &amp; Laptops
---

### Post by hkramski on 2007-10-13
Hi all,

I've got an old ThinkPad 600E I would like to prepare for my (computer novice) parents. Final internet connection will be done by dial-in, so the internal analogue modem mwave is a must.

The mwave module now loads fine. I also installed and configured the mwavem 2.0-2 package, which loads successfully.

However, I am unable to make any calls to an internet provider. Every time the modem tries to dial a number, the mwavem process crashes. On the other hand, the modem replies to simple commands like ATZ or ATI3, so the general (serial) setup seems to be ok.

When I start mwavem manually (not using /etc/init.d/mwavem) to better see the error messages, all looks well:

[INDENT]   root@grandl:~# /usr/sbin/mwavem /etc/mwavem/mwavem.conf
   Initializing mwave manager...
   Initializing modem specific code...
   Got configured startup speed:  64000...

   Checking configured speed...
   Setting modem speed...
   Loading modem DSP...
   mwave modem, STARTED...[/INDENT]

In another terminal, I can now use minicom to successfully talk to the modem...
[INDENT]
   Welcome to minicom 2.2

   OPTIONS: I18n
   Compiled on Mar  7 2007, 15:10:03.
   Port /dev/ttyS1
   
                  Press CTRL-A Z for help on special keys

   AT S7=45 S0=0 L1 V1 X4 &c1 E1 Q0
   OK
   ati3
   ThinkPad Modem v4.0
   OK
   atz
   OK[/INDENT]

... until I try for example

[INDENT]   atdt1234[/INDENT]

which immediately leads to

[INDENT]   Segmentation fault (core dumped)
[/INDENT]
on my first terminal.

(With some tracing enabled via mwavem.conf, the last lines read:

[INDENT]    mwmload::mwmLoadDialToModem entry
    mwmpool::mwmPoolAllocateCoreChunk entry
    mwmpool::mwmPoolTransferControlBlock entry
    mwmpool::mwmPoolTransferControlBlock exit
    mwmcntnd::mwmCntndAllocSegment entry
    mwmcntnd::mwmCntndAllocSegment exit
    mwmpool::mwmPoolTransferControlBlock entry
    mwmpool::mwmPoolTransferControlBlock exit
    mwmpool::mwmPoolTransferControlBlock entry
    mwmpool::mwmPoolTransferControlBlock exit
    mwmpool::mwmPoolTransferControlBlock entry
    mwmpool::mwmPoolTransferControlBlock exit
    mwmpool::mwmPoolAllocateCoreChunk exit
    mwmload::mwmLoadDialToModem ulFeaturesToLoad 1912d4ea hmodV34 0
    mwmload::mwmLoadV34 entry
    
    Segmentation fault (core dumped)[/INDENT]

Looks like mwavem dies when loading something like /usr/share/mwavem/v34.dsp into memory.)

Things I tried so far:
[LIST]
[*]checked for hardware conflicts using the bios configuration utility ps2.exe
[*]tried a non-default hardware (irq etc.) setup for serial-a and modem (IR port is disabled)
[*]excluded irq 3 and 10 in /etc/pcmcia/config.opts, so the pcmcia handler does not touch them
[*]disabled all sound related modules
[*]compiled and tried my own "ACP Modem (Mwave) Driver for Linux" (mwavem-2.0.tar.gz) from Sourgeforge without luck.
[/LIST]

I'm running the latest firmware available (INET36WW = 1.16, 11/20/99) and feisty (7.04). My boot options include "acpi=off pci=noacpi pnpbios=off vga=0x317".

Everything else works fine and fast, so I really like to stay with xubuntu (my first xubuntu experience btw - and a very nice one!)

No more ideas here now (yes, I think I searched the forums and a lot of other useful web page ;-)). Is someone using the 600e's mwave modem in a similar setup? Should I file an (x)ubuntu bug report? Or does anyone know about any better mwavem help resources?

TIA
[INDENT]   Heinz[/INDENT]

---

### Post by hkramski on 2007-10-16
Any TP 600E users out there?

[INDENT]Heinz[/INDENT]

---

### Post by hkramski on 2007-10-29
Just for the records: Some problem after upgrade to Gutsy (7.10)

---

