---
title: "dmraid no longer activating nvidia(fake) RAID"
date: 2007-02-25
forum: Hardware &amp; Laptops
---

### Post by d0rp on 2007-02-25
On my previous install, I had my nvidia raid working just fine, all I had to do was install dmraid and it worked, but after I reinstalled ubuntu, dmraid isn't giving me a /dev/mapper/nvidia_* anymore.

It does, however recognize the raid, but it's not activating it :

> $ sudo dmraid -r
/dev/sdb: nvidia, "nvidia_dadhgefe", stripe, ok, 488397166 sectors, data@ 0
/dev/sdc: nvidia, "nvidia_dadhgefe", stripe, ok, 488397166 sectors, data@ 0
/dev/sdd: nvidia, "nvidia_dadhgefe", stripe, ok, 488397166 sectors, data@ 0
/dev/sde: nvidia, "nvidia_dadhgefe", stripe, ok, 488397166 sectors, data@ 0
/dev/sdf: nvidia, "nvidia_dadhgefe", stripe, ok, 488397166 sectors, data@ 0


any ideas?

---

### Post by nyinge on 2007-02-28
What happens when you issue the following command:
```
 sudo dmraid -ay 
```

---

### Post by 3vi1 on 2008-03-21
I noticed this same thing while trying to setup a system using an Asus Striker II Formula MB yesterday.  dmraid -ay produces no errors, and dmraid -r (and -s) has the right output, but the /dev/mapper device never gets created.

I just went ahead an used softraid for now, but that's not going to be acceptable for the purposes of some dual-booters.

-J

---

### Post by Jove on 2008-04-07
This has been driving me slightly nuts since Fiesty's release (and it's persisted through Gutsy and doesn't seem to be fixed in Hardy beta's (up to 2.6.24-15) either). And yes, I know I should have raised it as a bug earlier, but I've just worked around it by booting into 2.6.20-12 which was the last kernel where it worked properly. My bad.  I've an ASUS P5N-E SLI board (which I think uses the 680i chipset). Anyway, I've configured RAID-1 across two WD SATA drives for dual-booting into XP. Prior to 2.6.20-12 I was able to detect this fakeraid device with dmraid. Since 2.6.22, however, dmraid -ay gives the following message in /var/log/messages:

device-mapper: ioctl: error adding target to table

dmraid -tay works, however, so something's being detected:

nvidia_acihdbbb: 0 976773166 mirror core 2 131072 nosync 2 /dev/sda 0 /dev/sdb 0

I've Googled around a bit and some people are talking about it being a problem with duplicate UUIDs, which indeed there are on my system. blkid gives:

/dev/sda3: UUID="4EECF9B0ECF99287" TYPE="ntfs" 
/dev/sdb3: UUID="4EECF9B0ECF99287" TYPE="ntfs" 

but as the type is NTFS, there's no easy way to change this UUID.

I can't really pin this down to a kernel bug or dmraid or devmapper, but there's something screwy somewhere :)

Would be very pleased to get any input or ideas. Any further info required, I'll be happy to post it here.

---

### Post by Jove on 2008-04-18
Little bit of extra info. I tried the same dmraid -ay on both the new Fedora 9 (which failed with the same error) and Knoppix 5.3.1, which uses 2.6.24 kernel - and it succeeded! So my very tentative assumption that it's a kernel bug introduced prior to 2.6.20 is wrong. udev? libdevmapper? dmraid? Hmmm... back to digging.

---

