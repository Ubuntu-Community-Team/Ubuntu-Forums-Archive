---
title: "HD only works as master"
date: 2006-04-02
forum: Hardware &amp; Laptops
---

### Post by entryname on 2006-04-02
Hi gang.

have Ubuntu installed on original 10GB hard disk that came with the machine. Inherited 15GB disk, and thought, I could have that as a second hard disk. Was told, yep easy peasy, just plug it in, away you go. Wrong wrong wrong.

:-k 

After a lot of changing plugs and jumpers around it seemed to come down to this: the BIOS will only see the original hard disk as being present if it is jumpered as the sole (single) disk. If I jumper it as master, even with the would-be slave disconnected and depowered, the BIOS can't see it at all. This does look quite clear - HDD auto detect option in BIOS pronounces nil size after a long pause when jumpered as master, but almost instantly produces three possible settings, one of which I'm now using, when jumpered as sole/single.

I can hear somebody saying, ah he's got the jumper in the wrong place, probably looking at the pins upside down, but the jumper for master goes in the middle thus making it impossible to get wrong.

The hard disk is listed by System - Administration - Disks as WDC AC310200R 9.56GiB [Windows 98, now uninstalled, saw 9.54GB]. GParted adds that it has 255 heads 63 sectors per track 1,247 cylinders giving a total size of 9782 MB. It also gives the disk type as msdos. The jumper WAS in the middle pair of pins (that is vertically in the centre, as shown for master). It is now horizontal on the second and third pins on the bottom row, which is how the label says it is often supplied for use as a single disk.

There are two (IDE) buses. One has the CDROM and the ZIP drive, both of which work (though the ZIP drive had to be manually fiddled, that's another story). The other bus as I type this, has the original hard disk jumpered as sole disk. 

Is it possible this hard disk simply won't work as anything other than a single? Could that be why the original IDE ribbon cable on that bus only had one plug on the drive end of it?

---

### Post by rfruth on 2006-04-02
Its very possible that the BIOS only supports one drive although two devices is the norm but in a all-in-one computer for example where a second drive is unlikely some manufacturers don't bother adding support for what would be physically impossible.

---

### Post by entryname on 2006-04-02
??? awww nurdles :( let me get this right. Even if the BIOS does show primary and secondary settings for two IDE busses, it might be that only the primary on one bus will actually work??

It does appear to attempt detection four times, twice per bus. How would I know if its not going to do two disks on the bus?? Is it just a case of, if it doesn't work and it's jumpered right, shrug and give up?

No chance that swapping one of the disks with a device from the other bus will get all four of them going is there??

---

### Post by entryname on 2006-04-09
Just a quick one. Now sorted. Changed 40 cable for 80. Changed boot sequence to put hard disk last. Re-did jumpers as per web diagram as I realised I had been looking at the pictures as they were on the drive label while it was mounted i.e. upside down as I was reading from the top. Now works.

---

