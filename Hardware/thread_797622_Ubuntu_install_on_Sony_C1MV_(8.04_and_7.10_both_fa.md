---
title: "Ubuntu install on Sony C1MV (8.04 and 7.10 both fail)"
date: 2008-05-17
forum: Hardware
---

### Post by pablolie on 2008-05-17
Hi -

I have edited out the quiet and splash options in the boot line to see where things hang as the install falls into 
(initramfs)...

It looks like it is an issue with the internal SCSI (even though it really is an IDE) drive, but perhaps the experts here can take a look at this...

[..] ACPI: unable to derive IRQ for device 0000:00:10.0
[..] ALI15x3: not 100% native mode: will probe irqs later
[..]  ide0: BM-DMA at 0x1400-0x1407, BIOS settings hda:pio hdb:pio
[..] ALI15x3: simplex device: DMA forced
[..]  ide1: BM-DMA at 0x1408-ox140f, BIOS settings: hdc:DMA hdd:DMA
[..] SCSI subsystem initialized
[..] Initialing USB Mass Storage Driver ...
[..] scsi0: SCSI enmulation for USB Mass Storage Devices
[..] usbcore: registered new interface driver usb storage
[..] USB Mass storage support registered
[..] Marking TSC unstable due to possible TSC hald in T2
[..] Time: acpi_pm clocksource has been installed
[..] scsi 0:0:0:0 direct access sony MSC-V02 1.00 PQ : 0 ANSI : 0 CCS
[..] driver 'sd' needs updating - please use bus_type methods
[..] sd 0:0:0:0 [sda] attached SCSI removable disk
[..] sd 0:0:0:0 attached scsi generic sg0 type o

Busybox v1.13 Debian 1:1.1.3 5ubuntu12 Built in shell (ash)
(initramfs)

...and there it stops.

Specs for the machine can be seen here
[http://129.33.22.12/release/specs/PCGC1MVM_mksp.pdf](http://129.33.22.12/release/specs/PCGC1MVM_mksp.pdf)

Anyone who could recommend
-further debugging tips
- boot options that may help
- BIOS information (there really isn't a lot there)

would get my huge gratitude!

---

### Post by pablolie on 2008-05-17
I also tried the alternagte CD that was text guided, and to go through the SCSI setup... no success. I guess I shall to have to give up on this?

I can not fin any information on the best driver or setup for the 20GB IBM Travelstar IC25N020ATDA04

---

### Post by pablolie on 2008-05-17
Wait a second! YEAH!

With the alternate CD (text guided) enter 
all_generic_ide floppy=off irqpoll
as te first items in the boot options (F6) and this seems to have installed Ubuntu 8.04 on a Sony Picturebook C1MV/M.

I do hope this helps other users - it is a neat little, superportable system that is highly usable with a nimble, good looking OS like Ubuntu. 

Ubuntu community - you guys are geniuses. Thanks, thanks, thanks SO MUCH for this alternative to the virus-infested, awkward and hyperinflated Microsoft OS. This ROCKS!

I am so proud to have this running on this little machine now. 

I hope this message helps out Sony Picturebook owners extending the lifetime of their systems with Linux Ubuntu.

And I am glad that I perhaps have made a little contribution to the project by persisiting and getting it to install, and documenting my experiences.

---

### Post by pablolie on 2009-11-07
I also want to tell any Sony C1 owners to stick to 8.04. I do not know why, but while 8.04 kind of works (albeit slowly), 9.10 *crawls* on the machine. it is unusable. stick to the 8.04 version at most.

---

