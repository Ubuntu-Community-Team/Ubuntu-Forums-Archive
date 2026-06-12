---
title: "SSD disk"
date: 2012-10-09
forum: Hardware
---

### Post by aeronutt on 2012-10-09
I'm thinking about getting a SSD for my Dell Vostro 3550 laptop. It's about 1.5 years old. A few questions:

Can I tell what speed the SATA controller can operate at? Current HD is 3.0Gb/s. (According to "sudo hdparm -I /dev/sda", the current HDD supports Gen 1 and Gen 2 speeds (1.5 and 3.0 Gb/s.)

Will the new 7.5mm SDD's fit in a 9mm 'slot'?

Anything particular in the SSD I should look for to insure it supports Ubuntu and multi OS boot?

---

### Post by papibe on 2012-10-09
> **aeronutt said:**
> Can I tell what speed the SATA controller can operate at?
Usually you can find those settings on the BIOS. The common values are 'legacy' and 'auto', for old drives and modern ones.
> **aeronutt said:**
> Will the new 7.5mm SDD's fit in a 9mm 'slot'?
Not as is. You need to buy a 2.5 to 3.5 conversion bay (they are pretty inexpensive BTW).
> **aeronutt said:**
> Anything particular in the SSD I should look for to insure it supports Ubuntu and multi OS boot?
If you either install Ubuntu first, or create the partitions with gparted, you are pretty much done (it will be aligned).

You may need to add post installation mounting options, to fully take advantage of your disk (read [here]("http://askubuntu.com/questions/1400/how-do-i-optimize-the-os-for-ssds")).

Hope that helps, and let us know how it goes.
Regards.

---

### Post by aeronutt on 2012-10-09
> **papibe said:**
> Usually you can find those settings on the BIOS. The common values are 'legacy' and 'auto', for old drives and modern ones.

Not as is. You need to buy a 2.5 to 3.5 conversion bay (they are pretty inexpensive BTW).

If you either install Ubuntu first, or create the partitions with gparted, you are pretty much done (it will be aligned).

You may need to add post installation mounting options, to fully take advantage of your disk (read [here]("http://askubuntu.com/questions/1400/how-do-i-optimize-the-os-for-ssds")).

Hope that helps, and let us know how it goes.
Regards.

Thanks, that does help. However, I'm not sure about the comment on the 2.5 to 3.5 conversion bay means.  My current HDD is 2.5", and I'm assuming it's 9.5mm thick because of the age and size of my laptop.  Newer HDD and SDD's are coming in 7mm thickness. IF I get a 7mm thick 2.5" SDD, will it fit w/o any problem in my 9.5mm 2.5" laptop slot.

---

### Post by papibe on 2012-10-09
:oops: Oops, I thought you had a Desktop.

I should fit. All 2.5" factor drives have the connectors and screw holes in the same side.

Regards.

---

### Post by m_duck on 2012-10-09
> **papibe said:**
> :oops: Oops, I thought you had a Desktop.

I should fit. All 2.5" factor drives have the connectors and screw holes in the same side.

Regards.

Yeah, as long as it screws in it should be fine, there just may be a gap under it. I upgraded my laptop to an SSD the other day - the drive I bought (Samsung 830 series) came with a small "adapter" to make the disk thicker if needed.

---

