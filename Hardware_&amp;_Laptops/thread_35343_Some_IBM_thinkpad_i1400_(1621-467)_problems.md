---
title: "Some IBM thinkpad i1400 (1621-467) problems"
date: 2005-05-18
forum: Hardware &amp; Laptops
---

### Post by niutonas on 2005-05-18
Hi all,

_[COLOR="Lime"]IBM thinkpad i1400 (2621-467) :)[/COLOR]_

Old, assembled ~1998 ?

ram: 128Mb
cpu: 433Mhz
hdd: 10Gb
agb: 4mb integrated
chipset: ali (alladin IV ?)

Runing Hoary  5.04 with gnome, xfce amd icewm.

Some hardvare problems:

a) ***********

problems compilling "tcptl" ]

I can't get it running ](*,)  and finally give up.

This laptop have no SMBIOS  :evil: so i don't know if 
it is any use try tu run "tcptl" :confused: .




b) **********

udma mode with  ali15X3 drivers

hdparm -i /dev/hda:

[COLOR="Silver"]Model=IBM-DJSA-210, FwRev=JS2OABDA, SerialNo=4209Z5K0730
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=DualPortCache, BuffSize=384kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=19640880
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 *mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4
 AdvancedPM=yes: mode=0xBF (191) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-5 T13 1321D revision 1:

 * signifies the current active mode[/COLOR]

and i can't get udma4:

if i using

hdparm -X68 /dev/hda

i get mesage like udma4 anabled;
 
/dev/hda:
 setting xfermode to 68 (UltraDMA mode4)

but 

cat /proc/ide/hda/settings
gives 

name                    value           min             max             mode
----                    -----           ---             ---             ----
****************************
current_speed           34              0               70              rw
****************************
 






the same problem with cd/dvd rom:
hdparm -i /dev/hdc output gives

 Model=TOSHIBA DVD-ROM SD-C2202, FwRev=1429, SerialNo=Y900003682
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=128kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 *mdma2
 UDMA modes: udma0 udma1 udma2
 AdvancedPM=no

can't make cd/dvd rom to use udma2.
only mdma2.





c) ************ 

can't get well working keyboarb:

numlock and other are not working

not working "Fn" keys except LCD contras and brightness.






d) ***********

HAL Device Manager 0.4.7

gives for bios, processor, memory, fdd

in device tab all blocks like : device, vendor and others
"Unknown"




e)**********

can't get direct rendering for my video card.
baced on Mach64. Is it usefull?

output of lspci  

0000:00:00.0 Host bridge: ALi Corporation M1621 (rev 05)
0000:00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller (rev 01)
0000:00:06.0 Communication controller: Lucent Microelectronics WinModem 56k (rev 01)
0000:00:07.0 ISA bridge: ALi Corporation M1533 PCI to ISA Bridge [Aladdin IV] (rev 0a)
0000:00:08.0 Multimedia audio controller: ESS Technology ES1969 Solo-1 Audiodrive (rev 02)
0000:00:0f.0 IDE interface: ALi Corporation M5229 IDE (rev 20)
0000:00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU] (rev 09)
0000:00:13.0 CardBus bridge: O2 Micro, Inc. OZ6812 Cardbus Controller (rev 05)
0000:00:14.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)

f)****************

can't get temperature or fan spead sensors data
by gnome or xfce panel plugins.

g)****************

on xfce can't lisen audio cd with Totem or Cdplayer.
Totem can't found or read "cdda" but Sound juicer can ripp without
problems.

On Gnome both programs are reading audio.
Only problem with Cdplayer: it makes litle stops every 1~2 second
but there is no problem with Totem.



h)*************

does kernell 2.6.10-5-686
by default configuration is good.
Or i need to recompille it?



i)*************

i am using network witch ask for identification.
Identification is by name and pasword
and entered in webpage (i think it's ssl routine or something like)

Is it posible in easy way to make automatic login to this network during boot?
And to keep possibillity to use other network? 

j)*************

total ram 128
cpu: 433 mhz 

so usualy i use xfce :)

But firefox is very difficult job for cpu:
the most bad is in starting firefox (It gets ~10-20s running cpu on 100%).

That are a lot problems :)

But in general Xfce gives new breath for this old laptop.

I will be thankfull for sugestions, solutions and coments:)

---

