---
title: "Desperate!! - Ubuntu on X41: HD very SLOW"
date: 2009-09-24
forum: Hardware
---

### Post by jiriki78xx on 2009-09-24
Hi all,

i'm writing to see if someone has a working solution to this problem: i've installed few time ago, the 9.04 ubuntu's version on my old laptop Thinkpad X41.
From the beginning i noticed the HD was extremely SLOW (being 4200 rpm it can't be a lightning :P ) and i started doing some tests with hdparm command. Following the results:

# hdparm -i /dev/sda

/dev/sda:

 Model=HTC426040G9AT00                         , FwRev=00P4A0L2, SerialNo=              EA1793
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=0kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=78140160
 IORDY=yes, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=yes: mode=0xFE (254) WriteCache=disabled
 Drive conforms to: ATA/ATAPI-6 T13 1410D revision 3a:  ATA/ATAPI-3,4,5,6

 * signifies the current active mode

from the output I noticed the DMA mode seems to working fine and the WriteCache option is disabled. When i try to set on both these option this is wath happens:

#hdparm -d1 -W1 /dev/sda
HDIO_SET_DMA failed: Inappropriate ioctl for device
HDIO_GET_DMA failed: Inappropriate ioctl for device

the disk's performances are really awful:

/dev/sda:
 Timing buffered disk reads:   24 MB in  3.66 seconds =   6.55 MB/sec

The controller is an Intel ICH6 (see lspci output attached:)

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)

googling around i found that this particular controller is giving several problems with Linux, and also on X41 model, cause it's a SATA controller that manage a PATA device (1,8 inch Hitachi HD).
So, at the end of the story, someone tells that some patches resolve the problem but the link was broken and in the later kernel it should be fixed. I made an attempt modifying th options in hdparm.conf and adding an extra option to the grub's kernel line, BUT UP TO NOW NOTHING WORKED....  [IMG]http://forum.ubuntu-it.org/Smileys/ubuntu-it/angry.gif[/IMG] 

Now I downloaded kernel 2.6.30 and at last i would recompile it adding the modules:
Device Drivers --> ATA/ATAPI/MFM/RLL support --> "generic ata/atapi disk support" - legacy /proc/ide support 
and also Intel PIIX/ICH chipset support....

I also tried with :
- other distro's live cd but with the same result... [IMG]http://forum.ubuntu-it.org/Smileys/ubuntu-it/cry.gif[/IMG]
- upgrading the disk's BIOS
- upgrading machine's BIOS

Someone could PLEASE HELP ME and tell me what to do in order to have my disk working at a decent speed???!!
I can't believe there is no way to install my dear ubuntu on X41 without the bottleneck caused by this disk.....
Thanks in advance!!

---

