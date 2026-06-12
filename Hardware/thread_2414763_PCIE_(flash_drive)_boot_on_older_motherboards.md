---
title: "PCIE (flash drive) boot on older motherboards"
date: 2019-03-14
forum: Hardware
---

### Post by Engineeringtech on 2019-03-14
Hi!

Very green Linux user here.   I know just enough to be dangerous.  I'd like to know if there are any schemes available that would allow the use of a PCIE flash drive to boot Ubuntu on my old gaming computer.  The hard drive died a few months ago.    I'd like to restore the computer to do some basic CAD work.  Nothing elaborate.  But I'd like to milk the hardware for as much performance as possible.   The hardware is getting a little old, but it was state of the art when I bought it in 2009.  It has plenty of memory, and an E8400 processor.   The Windows community will without discussion say the motherboard will not boot a PCIE drive,  But I am wondering, if there is any way to start the boot process with Grub on a SATA drive or USB stick, and pass control to the OS on a PCIE flash drive.  The use of the latter, should be much faster than SATA 2.  I have a free X16 PCIE slot.

Any advice would be appreciated.

---

### Post by him610 on 2019-03-14
Well, nobody wants to see good serviceable equipment just sitting there. The vintage hardware you have is a non-issue. I have three that date from 2008 with processors in the same generation as your e8400.
Personnaly, I am unfamiliarwith a PCIE flash drive. Is this what you are referring to, [https://www.newegg.com/Product/Product.aspx?Item=N82E16820167359](https://www.newegg.com/Product/Product.aspx?Item=N82E16820167359)
You *can* boot from a USB stick. You may need to develop a script to pass control to the PCIE flash drive. 
Are Linux drivers available for your PCIE device?  
You can also get a solid state drive host your chosen operating system on - they're pretty inexpensive right now.
Sounds like a worthwhile project, good luck.

---

### Post by Engineeringtech on 2019-03-14
Thanks.  :Sorry for the delayed response.   Had to leave the thread.  (I am working.)  Yes, that is the type of drive I am interested in.  They supposedly operate much faster than SATA 2 SSD's.   As I said though, I have little experience with Linux.  I'm not going to be able to write a script.    First task is to find out if anyone has done anything like this.  I know a PCIE flash drive can be accessed by Windows, once the machine is booted.   Motherboard manufacturer told me that.  I believe there are Linux drivers for PCIE flash drives.   What I want to know is if it is possible to get the boot process started on a SATA or USB drive, then load the drivers for the PCIE flash drive.

Incidentally, I was always surprised that motherboard and disk drive makers didn't get together on drives that could be installed in PCIE slots YEARS ago, before SSD's were even available.   Think of all the ugly, and unreliable cabling and connectors it eliminates. .

---

### Post by him610 on 2019-03-14
There are a couple of people that frequent these forums that are quite knowledgeable about the boot process. Maybe one of them will jump in. The fact these drives are available commercially makes me think there are probably drivers available. 
Several years ago I became interested in SCSI drives because they were more efficient so I bought a scsi drive, a scsi controller, and another device to serve as the scsi terminator. I learned a lot about scsi completing that project.
It is entirely possible you may be able to install your chosen operating system on the PCIE flash drive. If you already have this equipment, why not give it a try?

Reasons why PCIE flash drives are not the choice of the average consumer; however, they probably are with commercial companies: AWS, Google, and other data hosting server farms.
1. It occupies a scare resource, the PCIE slot. - There is normally only one or two.
2. More expensive than either HDDs or SSDs. - Consumers vote with their dollar$.
3. Being supplanted by newer technology, PCIE-NVME.... - Can be made faster, cheaper, smaller, more reliable.

You can buy a used one on eBay for a lot less than a new one. Unless one's processes are automated, most of the nonproductive cycles of a computer are spent waiting on the human behind the keyboard.

---

### Post by Engineeringtech on 2019-03-14
Thanks again.  I don't have the PCIE flash card yet.  They ARE expensive.  So I wanted to know if I had a ghost of a chance before buying.  I was big on SCSI years ago.  Initially, this same system booted from a SCSI drive connected to a controller plugged into the PCI bus (NOT PCIE).  Took drivers supplied by the SCSI controller manufacturer.  It was slow.  Not because of the drive (10k RPM), but because the PCI bus didn't have enough bandwidth.  I was going to buy a PCIE SCSI controller, but they were $400 at the time.  I ditched the SCSI drive and have been using an ATA drive on the SATA 2 ports.  Seems a shame to have a 16x PCIE connector unused.

Anyway, if they can boot a system from a drive connected to a PCI slot, seems lie with the right drivers, they could boot from a PCIE slot.

---

### Post by him610 on 2019-03-14
On my SCSI improvement project, I paid around $50 for a controller that fit in a PCI slot, $5 for a used 6GB SCSI drive, and $1 (from ebay) for a used SCSI Read-only CD drive to be the terminator. My controller had connections for both widths of SCSI cables; I believe I used the wider ribbon cables on mine. In the beginning I knew absolutely nothing about SCSI; had to do a good bit of research on it, but I learned a lot. Once installed and configured, I used that SCSI drive just like a regular hard drive.

You know that if you order a PCIE flash card/drive then can't get it to work, you can always return it.

---

### Post by Engineeringtech on 2019-03-15
Maybe you got surplus drives.SCSI equipment?   They have come down in price considerably since I was using them on Macintosh servers and my gaming computer.  Probably because very few people are using them anymore. 

 I seem to make bad decisions on computers.  I paid $200 each for the three 10K RPM wide drives I initially used in a RAID array on the gaming computer.     Lasted me about a month.  Controller failed.   Good cooling  Surge protected.  I ditched the SCSI drives I spent two weeks salary on, and bought three ATA drives intending to put THEM in a RAID array.  Never worked.  I had to fight with the store to take back the SATA RAID controller.  

Companies have frequently reneged on their "money back", and warranty promises.  So I don't buy unless it has a reasonable chance of success.      I suspected right from the get go that I had problems with the motherboard Ethernet and SATA ports.  But once it was out of the box, Newegg wouldn't take it back.   It was 2009, shortly after the economy crashed.  Gigabyte and other motherboard companies stopped making that generation of motherboard.  The supply dried up overnight.  They couldn't (or wouldn't) exchange it.  I could have bought a newer generation motherboard, but then I would have had to ditch my unused processor, and RAM.   So I have been fighting with this motherboard every since, replacing SATA hard drives that keep failing.  Yes, I have replaced 3 SATA drives in nine years.  Considering I only used the computer about an hour a month, I haven't gotten much use out of them.    I guess eventually I will have to eat my losses.  But I wanted to see if I could milk some life out of the box I have invested so heavily in.

---

### Post by oldfred on 2019-03-15
For the cost of those drives, I would buy a new better motherboard and NVMe drive(s).

My old 2006 system with new motherboard in 2009, due to nVidia card failure was upgraded with a tiny small 60GB SATA SSD just for boot in 2011. That SSD was just a bit faster than then new HDDs, but a lot faster than my old 160GB slow drives from 2006.
But that improved system enough that I did not get new UEFI system until about 2014.

My concern is if you can boot from that drive or have to use some sort of work around.
A lot of older systems, do not have the boot flexibility that newer systems have. I would see what your manual says on support.

---

### Post by sudodus on 2019-03-16
I would boot from an SSD connected via SATA. Maybe it would also be big and fast enough for your data files.

I would not spend big money on a device, that might or might not work. It is different if you have it already.

Are you sure that you benefit from a very high-speed PCIE flash drive? Do you know that the drive read or write speed will be the bottleneck for the tasks that you want to run?

---

### Post by oldfred on 2019-03-17
It may be interesting to see if this user can get his NVMe with PCIe to NVMe adapter working.
[https://askubuntu.com/questions/1126456/wd-sandisk-nvme-m-2-stick-not-quite-working](https://askubuntu.com/questions/1126456/wd-sandisk-nvme-m-2-stick-not-quite-working)
[https://www.amazon.com/dp/B01N78XZCH/?tag=stackoverfl08-20](https://www.amazon.com/dp/B01N78XZCH/?tag=stackoverfl08-20)

---

### Post by Engineeringtech on 2019-03-18
Thank you for all your advice.

---

