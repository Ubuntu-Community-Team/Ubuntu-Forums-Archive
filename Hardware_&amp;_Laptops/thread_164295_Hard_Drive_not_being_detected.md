---
title: "Hard Drive not being detected"
date: 2006-04-22
forum: Hardware &amp; Laptops
---

### Post by kupad on 2006-04-22
One of my hard drives is not being detected, and as a result I can't mount any of its partitions.  The hard drive mounts fine on another distro (Mandrake 10.1), so I know the drive itself is working fine.

On boot up I received the following messages:

irq 10: nobody cared (try booting with the "irqpoll" option
[<d886f4a07>] (ide_intr+0x0xed[ide_core])
Disabling IRQ#10
Buffer I/O error on devide hdf

So, I went ahead and added the "irqpoll" option in grub (/boot/grub/menu.lst).  

Nothing Changed.


Dmesg has many of these: 

[4294732.895000] end_request: I/O error, dev hdf, sector 71
[4294732.895000] end_request: I/O error, dev hdf, sector 64
[4294732.895000] end_request: I/O error, dev hdf, sector 65
[4294732.895000] end_request: I/O error, dev hdf, sector 66
(and so on...)


lspci:

0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:07.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:0f.0 Unknown mass storage controller: Promise Technology, Inc. PDC20262 (FastTrak66/Ultra66) (rev 01)
0000:00:10.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
0000:00:11.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
0000:00:11.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 07)
0000:01:00.0 VGA compatible controller: 3Dfx Interactive, Inc. Voodoo 3 (rev 01)

That "unknown mass starage controller" is there when I run lspci on Mandrake where the drive works, so it probably doesn't mean all that much.

lshw -C disk:

 *-storage
             description: Unknown mass storage controller
             product: PDC20262 (FastTrak66/Ultra66)
             vendor: Promise Technology, Inc.
             physical id: f
             bus info: pci@00:0f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: storage bus_master
             configuration: driver=Promise_Old_IDE
             resources: ioport:1420-1427 ioport:1414-1417 ioport:1418-141f ioport:1410-1413 ioport:1080-10bf iomemory:f4000000-f401ffff irq:10
           *-ide
                description: IDE Channel 0
                physical id: 2
                bus info: ide@2
                logical name: ide2
                clock: 33MHz
              *-disk:0
                   description: ATA Disk
                   product: QUANTUM FIREBALLP LM20.5
                   vendor: Quantum
                   physical id: 0
                   bus info: ide@2.0
                   logical name: /dev/hde
                   version: A35.0700
                   serial: 184005856438
                   size: 19GB
                   capacity: 19GB
                   capabilities: ata dma lba iordy smart security pm
                   configuration: mode=udma4 smart=on
              *-disk:1
                   description: ATA Disk
                   product: ST340823A
                   vendor: Seagate
                   physical id: 1
                   bus info: ide@2.1
                   logical name: /dev/hdf
                   version: 3.54
                   serial: 6EF00AJL
                   size: 37GB
                   capabilities: ata dma lba iordy smart security pm
                   configuration: smart=on

It's worth noting that this is not exactly the same output I get on the other distro, which is the same everywhere but the last line here:

*-disk:1
                   description: ATA Disk
                   product: ST340823A
                   vendor: Seagate
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb                          <== trivially different (I think)
                   version: 3.54
                   serial: 6EF00AJL
                   size: 37GB
                   capacity: 37GB
                   capabilities: ata dma lba iordy smart security pm
                   configuration: mode=udma4 smart=on               <==== different


That missing "mode=udma4" might be part of the issue, I'm not sure.

Also, the kernel modules I have loaded on ubuntu differ significantly from the other distro. 

Here's lsmod | grep ide (from ubuntu):

ide_disk               16128  5
ide_cd                 36996  0
cdrom                  33952  1 ide_cd
ide_generic             1664  0
ide_core              125268  6 ide_disk,usb_storage,pdc202xx_old,ide_cd,ide_generic,piix

That pdc202xx_old was added to "/etc/modules" in an attempt to solve the issue.


--Phil

---

### Post by dglnz on 2006-05-07
Hi there,

Not a knowledgable user any any means but was wondering if you've put the command no irqpoll on the linux image line in your boot loader (grub menu.lst) eg...

Linux-2.6-12-XXX blah  noirqpoll splash 

I had a problem with the new kernal in breezy not booting and went to the IRC forums and was told in @ 30 minutes that i had to add the word IRQPOLL onto the linux image on grub menu.lst for me to get the thing to run.

why, Well i've got an old PC namely Aptiva AMD 500Mhz cpu, Hoary worked out of the box breezy and all sbsequent kernal images (at that time needed the irqpoll inserted for it to work.

hope it might help in a small way.

---

