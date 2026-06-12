---
title: "Standard Microsystems Corp. 9-in-2 Card Reader"
date: 2008-06-27
forum: Hardware
---

### Post by davidmaxwaterman on 2008-06-27
Hi,

I have a Dell monitor that has an integrated 9-in-2 card reader.

I am trying to get it to read a microSD card - I have the two adapters to take it up to full SD card size.

lsusb says :

Bus 006 Device 007: ID 0424:2228 Standard Microsystems Corp. 9-in-2 Card Reader

and if I run device manager, I see two SCSI devices on a USB Device; one is a 'CompactFlash Drive' and one is a 'Mass Storage Drive", and they're /dev/sdb and /dev/sdc respectively.

If I plug the card in, it seems click ok (on a latch, so that if I click it again, it comes out), I don't get any messages (in syslog or messages) about anything being plugged in.

If I try to mount it it says 'no medium found', and if I try to 'mkfs /dev/sdc' it says 'no medium found while trying to determine filesystem size'.

Does anyone have any ideas how to access this from 8.04?

Thanks,

Max.

---

### Post by timcredible on 2008-06-27
a microsd card only needs 1 adapter to make a normal sd card, what exactly are you using that has 2 adapters?  looks like the system sees the reader, but if the system saw an sd card, it would put an sd card icon the desktop and open the card in a new nautilus window.  so, i would look at the adapters as the culprit (i'm assuming you know the microsd card is good because you can use it on your cellphone or whatever?).  you can probably buy a microsd->sd adapter for about $3US on ebay.

---

### Post by davidmaxwaterman on 2008-06-27
> **timcredible said:**
> a microsd card only needs 1 adapter to make a normal sd card, what exactly are you using that has 2 adapters? 


I use a microSD->miniSD adapter and a miniSD->SD adapter.

> looks like the system sees the reader, but if the system saw an sd card, it would put an sd card icon the desktop and open the card in a new nautilus window.
so, i would look at the adapters as the culprit (i'm assuming you know the microsd card is good because you can use it on your cellphone or whatever?).  you can probably buy a microsd->sd adapter for about $3US on ebay.

Well, I haven't tried the new card in a phone, but I did try the existing card that I use in my phone with the same result. (I want to copy the contents of the card I'm using onto the newer, bigger card)

I think I saw another pile of adapters around the office somewhere so I'll give that a try when I get back there.

Thanks,

Max.

---

