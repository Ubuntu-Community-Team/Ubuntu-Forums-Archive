---
title: "lshw lists capabilities, but what do they mean?"
date: 2006-12-18
forum: Hardware &amp; Laptops
---

### Post by dief-eh? on 2006-12-18
Hello list!

I've just discovered the lshw command, and boy! does it ever lay stuff out. woohoo! But when the list mentions stuff like "capabilities", there's a lot listed that I have no clue about. I've tried searching these forums, and google dumps out way more info than I can digest before, oh say, 2020, so I am wondering how can I learn what the capabilities listed represent? My hard drive, e.g.:

*-disk
                   description: ATA Disk
                   product: Maxtor 6E040L0
                   vendor: Maxtor
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: NAR61GA0
                   serial: E1SRN4PE
                   size: 37GB
                   capacity: 37GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma6 smart=on

When I plug "ata" into google, for instance, I get:

...loads of info, but nothing to explain what ata provides, or what it stands for. Admittedly, my google skills bite.

As always, thanks for any response, and I hope this forum is the right one to post to.

---

### Post by zgornel on 2006-12-18
This might help : [http://en.wikipedia.org/wiki/Advanced_Technology_Attachment](http://en.wikipedia.org/wiki/Advanced_Technology_Attachment) . 
Usually the lshw information is not entirely useful. For information I'd recommend a computer architecture/periferal book or search the net for individual components like (cpu, busses, memory, northbridge, southbridge, hard disk, interface, PS2, USB, firewire, lcd, crt, ISA, PCI, MCA, video card etc.) Wikipedia is starting to be a reliable source so you can do a little bit of research there. If you want specific details about something post them on the forum. You might just get lucky

---

### Post by dief-eh? on 2006-12-21
> **zgornel said:**
> This might help : [http://en.wikipedia.org/wiki/Advanced_Technology_Attachment](http://en.wikipedia.org/wiki/Advanced_Technology_Attachment) . 
Usually the lshw information is not entirely useful. For information I'd recommend a computer architecture/periferal book or search the net for individual components like (cpu, busses, memory, northbridge, southbridge, hard disk, interface, PS2, USB, firewire, lcd, crt, ISA, PCI, MCA, video card etc.) Wikipedia is starting to be a reliable source so you can do a little bit of research there. If you want specific details about something post them on the forum. You might just get lucky

Thanks v. much for your reply. The Wikipedia url you supplied *was* helpful. I had an AT, in fact, long ago now, and as soon as I saw the wiki entry, whatever memory synapse that was snoozing in my cranium, woke up like the doormouse at the tea party and said "I knew that!" (before falling asleep again...)

---

