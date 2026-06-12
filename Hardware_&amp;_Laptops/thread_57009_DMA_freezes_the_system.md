---
title: "DMA freezes the system"
date: 2005-08-14
forum: Hardware &amp; Laptops
---

### Post by cobelloy on 2005-08-14
Hi again

I have a new LG DVD-RW and an old DVD-rom (unknown brand). 

I used to have an old P2 with the DVDrom and it was DMA enabled (but still didn't play video too good because of the slow computer). Now I have a P4 (2Ghz) with the new drive and the old one (hdc and hdd) but if I enable dma on either of them the system freezes and I have to press the reset button on the case, but without dma the video is terrible (really jumpy). 

Both drives are detected in bios and set at pio - 4 and 32-bit IO on (although I dont know what that means) so I have used hdparm -p 4 /dev/hdc and then also hdparm -c 1 /dev/hdc to set PIO at 4 and 32-bit IO as on, but enabling dma still causes a freeze. The video playback after -p and -c is good enough for me but not really perfect (still a little jumpy here and there) but the drives are not recognised by DVD-decrypter (wine) because it requires dma (apparently)

the motherboard is an ECS brand with a SIS chipset, onboard sound and graphics seem to be fine, so I assume this means that the chipset is working OK with the kernel?

can anyone help?

---

### Post by yaye on 2005-08-14
[QUOTE=cobelloy]........Both drives are detected in bios and set at pio - 4 and 32-bit IO on (although I dont know what that means) so I have used hdparm -p 4 /dev/hdc and then also hdparm -c 1 /dev/hdc to set PIO at 4 and 32-bit IO as on, but enabling dma still causes a freeze...............can anyone help?[/QUOTE]

Hello,

PIO mode is an older transfer mode:

[http://www.pcguide.com/ref/hdd/if/ide/modes_PIO.htm](http://www.pcguide.com/ref/hdd/if/ide/modes_PIO.htm)

DMA is the newer, faster mode:

[http://www.pcguide.com/ref/hdd/if/ide/modesDMA-c.html](http://www.pcguide.com/ref/hdd/if/ide/modesDMA-c.html)

I think you are having the freeze because you are telling them to run in two different modes, or the drives don't support DMA.

Ian

---

### Post by cobelloy on 2005-08-15
hi - thanks for the response, I have tried setting PIO to 0 in bios, but still the computer freezes when I enable dma, really tearing my hair out about this - havn't looked at those links yet though - kind of busy, will look at them in depth tomorrow, meanwhile, any other info would be much appreciated

thanks

---

### Post by yaye on 2005-08-15
[QUOTE=cobelloy].......I have tried setting PIO to 0 in bios, but still the computer freezes when I enable dma, really tearing my hair out about this.......any other info would be much appreciated.[/QUOTE]  

I think it's one or the other ( PIO or DMA ), not both.  DMA mode ( Direct Memory Access ) has the drive communicate directly with memory, CPU is not invovled.  PIO mode has the CPU control the transfer of data between the drive and memory.  

Have you tried setting the transfer modes in the BIOS to DMA mode?  If it is not an option, that may be the problem, the system board doesn't support DMA mode.  PIO 0 is the slowest mode, it does not turn PIO mode off.  I have SCSI optical drives and an old system so I can't check my settings as a comparison for you.

If the BIOS has Auto as an option, set it to that and the BIOS will communicate with the drives and determine the fastest mode that is compatible with both the drives and the system board.  Good Luck.

Ian

---

### Post by cobelloy on 2005-08-16
OK, 

PIO needs to be disabled to use DMA ?

well, in BIOS, the only options for PIO are, 0,1,2,3,4 or auto, and the only other thing I can set is 32 bit mode to on or off. I have tried all combinations of PIO mode + 32 bit and still enabling DMA causes a terminal system freeze, that is to say, the system freezes as soon as I try to access the dvd device itself, nothing unusual happens after actually setting DMA to on.

is there a way to explicitly disable PIO with hdparm? The -p option specifies the PIO mode to use (0-4), but what about disable?

the motherboard manual says that the IDE controller is capable of DMA/UDMA, and the info for the dvd drives also say UDMA 2 for one of them UDMA 2 or 4 for the other, I am using the newest IDE cable I have, so it should be a DMA capable cable.

remember also that one of these drives (currently the slave to the brand new LG HL-DT-ST DVDRAM GSA-4163B, previously slave to an LG CD-RW) was working fine in DMA mode with my old P2 mobo/cpu, but neither will work in DMA mode with the P4 mobo/cpu

I have explored flashing the bios on the motherboard - but the info suggests no improvements that I need (since the chipset is supposed to be DMA capable anyway) and the process is a little obscure at present since it involves a windows flash utility. Also looked at dvd drive firmware, and I have the latest firmware already.

What can I do ??? This can't possibly be the end of the line, I need to use DMA

any ideas out there?

---

### Post by yaye on 2005-08-16
[QUOTE=cobelloy].......I need to use DMA.........any ideas out there?[/QUOTE]

From my Award 4.59 BIOS Integrated Peripherals Section:

IDE HDD Block Mode: Enabled
On-Chip Primary PCI IDE: Enabled
On-Chip secondaryPCI IDE: Enabled
  IDE Primary Master PIO: Auto
  IDE Primary Slave PIO: Auto
  IDE Secondary Master PIO: Auto
  IDE Secondary Slave PIO: Auto
  IDE Primary Master UDMA: Auto
  IDE Primary Slave UDMA: Auto
  IDE Secondary Master UDMA: Auto
  IDE Secondary Slave UDMA: Auto

In short, enable both On-board IDE controllers, set PIO and DMA to Auto.  The BIOS communicates with the drives to determine the optimal settings.

Ian

---

### Post by cobelloy on 2005-08-17
my bios doesn't allow all of those things to be set, but I have tried all variations of PIO and also tried setting the PCI IDE to both or auto, no change

BUT

had a brainwave - checked hdparm on hda and found that dma is on, also bios shows pio enabled to 4 on hda too - so I tried both dvd devices as secondary masters on their own, no change, then tried them as primary slaves (to hda) and wouldn't you know it... DMA works just fine!

am I to assume now that the secondary IDE bus is stuffed in some way?

if it is - I can live with that, as long as I have one correctly functioning dvd device I am happy, the secondhand P4 mobo/cpu/ram was pretty cheap and is a gigantic improvement on my P2 in pretty much every other way

thanks for all your help and suggestions on this - I guess it was really an unsolvable dilemma after all

---

### Post by yaye on 2005-08-17
[QUOTE=cobelloy]................thanks for all your help and suggestions on this - I guess it was really an unsolvable dilemma after all[/QUOTE]

You're welcome. When I help friends and family with their computers, I always put the hard drive(s) on the primary IDE controller.  The optical drive(s) go on the secondary IDE controller. One of the optical drives as Master, the other as Slave.

Ian

---

### Post by Cuppa-Chino on 2005-11-25
hmm I am having similar albeit maybe more random problems ...

am posting here as I cannot think of what it could be but the 32bit mode...

have Asus P4P800 MoBo with P4 2.4GHz 1 IBM IDE0 HD & 1 Samsung SATA drive, 1 Pioneer DVD Rom IDE1-Slave & 1 Mitsumi CDRW IDE1-Master etc etc...

all working more or less fine (in Windofs, memtest my system is rock solid etc) but ever since I have upgraded the kernel to 2.6.12-10-686-smp and turned on DMA & 32bit transfer more it has been really random (it had random moments even before then)...

:arrow: sometimes system is fine, sometimes it does not boot up, sometimes it freezes....
*_any ideas?_*

---

