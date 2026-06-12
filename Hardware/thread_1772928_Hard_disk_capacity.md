---
title: "Hard disk capacity"
date: 2011-06-01
forum: Hardware
---

### Post by lordpaladin on 2011-06-01
can ubuntu especially natty 64 bit support 1 - 1.5TB internal hard disk?

thanks

---

### Post by munzerelli on 2011-06-01
yes

---

### Post by psusi on 2011-06-01
And far larger.

---

### Post by sanderj on 2011-06-01
> **psusi said:**
> And far larger.

Yes, but above 2TB you will need:

[LIST=1]
[*]Hardware that supports/understands >2TB drives
[*]GPT (GUID Partition Table) instead of MBR (or use 4KB sectors with MBR, possibly causing incompatibilities with some tools)
[*]an UEFI BIOS if you want to boot off a >2TB disk (/partition?)
[/LIST]

See [http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html) for more info on >2TB disks.

---

### Post by srs5694 on 2011-06-01
> **sanderj said:**
> Yes, but above 2TB you will need:

A correction: The limit is 2 TiB (2x2^40 bytes), not 2 TB (2x10^12 bytes). Disk manufacturers invariably use the power-of-10 units, and AFAIK all current "2 TB" drives are pretty close to that value, which is enough below 2 TiB (about 2.2 TB) to cause no problems for MBR.

> 
1. Hardware that supports/understands >2TB drives


I've heard of this being a problem with some USB docking stations. I've not heard of a computer that has an SATA interface that can't handle such drives, but of course that doesn't mean that computers or interfaces that can't handle the drives don't exist. I'm not sure what the SATA protocols specify in terms of the number of bits used to address sectors. If there's a protocol version that specifies 32-bit sector addresses, it could be an issue. If all the protocols support higher values, it shouldn't be a problem, at least theoretically.

> 3. an UEFI BIOS if you want to boot off a >2TB disk (/partition?)

I've seen this claim before, but I'm not convinced it's real, at least not when applied to whole disks. The reason for my skepticism is that there have been BIOS limits in the past (504 MiB, ~8 GiB, and 128 GiB, IIRC). These limits have always applied to the boot loader's ability to read files from the disk, and it's always been possible to boot from a disk bigger than the limit by ensuring that the critical boot loader files reside below the limit. In Linux, this has typically been done by creating a /boot partition that's below the limit.

That said, I've never experimented with an over-2TiB disk to be sure what restrictions actually apply. If somebody cares to send me such a disk, I'll be happy to experiment with it. ;)

---

### Post by psusi on 2011-06-01
> **srs5694 said:**
> I'm not sure what the SATA protocols specify in terms of the number of bits used to address sectors.

48 bits.  Disks are allowed to use only 24 bits if they want, but 48 bit is recommended and the controllers have to support it.

I read the SATA and SAS protocol specs a few months back.  Really interesting stuff.  They use the same physical layer so you can actually plug a SATA disk into a SAS controller.  I really want to get some SAS hardware to play with.

---

### Post by sanderj on 2011-06-01
> **srs5694 said:**
> 
I've heard of this being a problem with some USB docking stations. I've not heard of a computer that has an SATA interface that can't handle such drives, but of course that doesn't mean that computers or interfaces that can't handle the drives don't exist. I'm not sure what the SATA protocols specify in terms of the number of bits used to address sectors. If there's a protocol version that specifies 32-bit sector addresses, it could be an issue. If all the protocols support higher values, it shouldn't be a problem, at least theoretically.


Some 3TB harddisks are sold together with a PCI-SATA-controller to take care of the 3TB. See for example [http://news.cnet.com/8301-17938_105-20019961-1.html](http://news.cnet.com/8301-17938_105-20019961-1.html)

Apparantly there is hardware that can not handle the 3TB.

---

### Post by srs5694 on 2011-06-01
> **psusi said:**
> 48 bits.  Disks are allowed to use only 24 bits if they want, but 48 bit is recommended and the controllers have to support it.

24 bits works out to 8 GiB, and 48 bits to 128 PiB, so no truly modern disk could use a 24-bit limit and the 48-bit limit is so far above current disk sizes that it's not going to be an issue.

> I read the SATA and SAS protocol specs a few months back.  Really interesting stuff.  They use the same physical layer so you can actually plug a SATA disk into a SAS controller.  I really want to get some SAS hardware to play with.

Yes, SATA and SAS are an attempt to move toward integrating the old IDE and SCSI worlds (among other things, of course).

[quote=sanderj]Some 3TB harddisks are sold together with a PCI-SATA-controller to take care of the 3TB. See for example [http://news.cnet.com/8301-17938_105-20019961-1.html](http://news.cnet.com/8301-17938_105-20019961-1.html)

Apparantly there is hardware that can not handle the 3TB.[/quote]

Yes, I've heard of that. I'm suspicious that it's actually a hardware issue, though, especially given the limits that psusi quotes. It could be that some motherboards have BIOS limitations; by attaching the drive to a separate controller, the controller's firmware would take over, bypassing any flaky BIOS.

---

### Post by psusi on 2011-06-01
> **sanderj said:**
> Some 3TB harddisks are sold together with a PCI-SATA-controller to take care of the 3TB. See for example [http://news.cnet.com/8301-17938_105-20019961-1.html](http://news.cnet.com/8301-17938_105-20019961-1.html)

Apparantly there is hardware that can not handle the 3TB.

Just because someone tries to sell you something doesn't mean you need it ;)

I have not heard of anyone having such an issue, and based on what I know about SATA, it isn't possible.  That being that there are 3 8 bit registers in the controller that the address is written to ( twice for 48 bit address mode ), which are then sent to the drive in what the SATA standard calls a FIS ( Frame Information Sequence ), but essentially is a packet.

> **srs5694 said:**
> 24 bits works out to 8 GiB, and 48 bits to 128 PiB, so no truly modern disk could use a 24-bit limit and the 48-bit limit is so far above current disk sizes that it's not going to be an issue.

Bingo.


> **srs5694 said:**
> Yes, I've heard of that. I'm suspicious that it's actually a hardware issue, though, especially given the limits that psusi quotes. It could be that some motherboards have BIOS limitations; by attaching the drive to a separate controller, the controller's firmware would take over, bypassing any flaky BIOS.

Good point.

---

