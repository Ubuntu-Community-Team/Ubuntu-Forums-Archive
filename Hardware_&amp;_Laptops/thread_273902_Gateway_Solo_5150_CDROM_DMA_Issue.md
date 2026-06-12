---
title: "Gateway Solo 5150 CDROM DMA Issue"
date: 2006-10-09
forum: Hardware &amp; Laptops
---

### Post by MistaED on 2006-10-09
Hey all, I currently have a Gateway solo 5150 here which I want to install kubuntu 6.06. The specs are:

266mhz Celeron (it says pentium II on the sticker but proc cpu says otherwise ;) )
128mb ram
Neomagic video chip & some old legacy ISA ES1688 sound chip

Yes I know KDE isn't very wise to put on and I should go with some lame windowmanager setup but I reckon I can get it to function well once tweaking some things ;)

Now with this machine I always needed to specify nodma on the CD-ROM because it is utter junk unless it is working in PIO mode. Now I chuck in the alternate kubuntu install CD in and put nodma on the end of the kernel boot string hoping it will work. The hard drive can work in DMA just fine though.

At first it does work, but once the installer starts probing around for hardware, it re-enables DMA onto the CD-ROM even though it detected that the bios is set for it to PIO mode (I viewed the dmesg in one of the terminals to find a whole bunch of lost interrupts due to /dev/hdc running in DMA mode).

The mobo chipset in this machine is a 440BX/ZX/DX PIIX4 IDE, so it is a very common setup for old Celeron/Pentium II/III chips, so I am wondering can I perhaps specify a nodma string to the end of that boot line for the piix4 module?

Cheers
-MistaED

---

### Post by arava on 2006-10-12
Hello MistaED:

I have a couple of machines with Asus motherboards. I'm guessing the problem with Ubuntu is it doesn't seem to like the PIIX4 southbridge chip.

I may have a similar problem.
[http://ubuntuforums.org/showthread.php?t=273015](http://ubuntuforums.org/showthread.php?t=273015)
[http://www.ubuntuforums.org/showthread.php?t=264705](http://www.ubuntuforums.org/showthread.php?t=264705)
[http://ubuntuforums.org/showthread.php?t=267949](http://ubuntuforums.org/showthread.php?t=267949)

Unfortunately nobody has answered my questions in all three forums.
Another person with similar problems has recommended forgetting about Ubuntu and trying another distribution because of a lack of help.

I'm still hoping someone would be kind enough to give me a clue as to where to start looking for the solution. It is a shame to waste perfectly good machines; throwing them out just pollutes our environment.

---

