---
title: "hdparm - sigh"
date: 2005-04-26
forum: Hardware &amp; Laptops
---

### Post by danx on 2005-04-26
Hi,

Just discovered and installed (k)ubuntu but can't enable dma on the dvd drive. :(  A google suggested to reorder /etc/module but that didn't work.  Then i tried moving hdparm to later in the boot sequence.  Still have the problem.

sudo hdparm -d1 /dev/hda 

> /dev/hda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)

During the boot sequence it says /dev/hda not found.  This is the command in /etc/hdparm.conf

> /dev/hda {
	mult_sect_io = 16
	write_cache = off
	dma = on
}

I did sudo mv S07hdparm S22hdparm as per some advice on web, but still no joy  ](*,) 

The system is AMD64 NForce4 running the 686 kernel, with 2 SATA hard drives and a dvd rw.


Any ideas? O:) 


Thanks,
Danx

---

### Post by denzilla on 2005-04-26
This is what I added to my bootmisc file to fix my woes :)

hdc = 2nd IDE master
hdd = 2nd IDE slave

---

### Post by danx on 2005-04-27
[QUOTE=denzilla]This is what I added to my bootmisc file to fix my woes :)

hdc = 2nd IDE master
hdd = 2nd IDE slave[/QUOTE]

Thanks I just tried that.  No dma :(

Went over the bios settings,  they look fine.  This is really annoying.  ](*,)

---

### Post by danx on 2005-04-27
[QUOTE=danx]Thanks I just tried that.  No dma :(

Went over the bios settings,  they look fine.  This is really annoying.  ](*,)[/QUOTE]

Wasn't using the right chipset module. :-#

---

### Post by Turin Turambar on 2005-04-27
Hda is usually a Ubuntu partition. I doubt that your DVD is on hda. I guess it's on hdd or hdc. If in doubt, go to /dev/ directory and find "dvd" or "cdrom" and see the link target.

I also got a "not found" message on the boot for my dvd/cdrom, but it turned DMA on, no matter what.

---

### Post by danx on 2005-04-27
The primary partitions are on sata drives, and fall under /dev/sd*.  The only ide drive is the dvd.

---

### Post by denzilla on 2005-04-27
[QUOTE=danx]Thanks I just tried that.  No dma :(

Went over the bios settings,  they look fine.  This is really annoying.  ](*,)[/QUOTE]

Sorry it didn't work for you :( Did you check them after reboot. correct?

---

### Post by danx on 2005-04-28
Yeah.  It turns out it was the chipset module... adding amd7xx at the start of /etc/modules worked.  I had looked up the module with lsmod before and it was loaded, so i didn't think that was the problem.  Perhaps it wasn't just wasn't loaded early enough.

---

