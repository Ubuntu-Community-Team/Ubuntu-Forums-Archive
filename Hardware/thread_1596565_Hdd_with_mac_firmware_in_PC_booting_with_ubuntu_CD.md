---
title: "Hdd with mac firmware in PC booting with ubuntu CD?"
date: 2010-10-14
forum: Hardware
---

### Post by Horza on 2010-10-14
I've got an hdd from a mac, with mac firmware on it, whose contents I would like to read by putting in a non-mac laptop (compaq 6710b) laptop, and booting the lappie from an ubuntu 9.04 CD; does anyone know whether this would work, or, especially, that it wouldn't mess up the HDD?

These laptops have an HDD controller that is incompatible with some cloning programs, although they boot fine off ubuntu boot CDs; it strikes me as possible that the mac firmware might however produce a problem.

 Thanks.

---

### Post by srs5694 on 2010-10-14
I've never before heard of internal hard drives having Mac vs. non-Mac firmware. The closest I've heard to that is firmware being tweaked for certain embedded devices (like TiVos), but that only adjusts certain performance parameters and doesn't affect compatibility; and some external drives come with OS-specific virtual partitions, but that also doesn't affect their ability to be used with other OSes.

If you're *certain* that the drive has Mac-specific firmware, then I'd be interested in a link to more information on this. If not, I wouldn't worry about it; just plug the drive in and use the Ubuntu live CD to access it. (Ubuntu does include drivers for the HFS+ filesystem used by modern Macs, although it will most likely be read-only since it's probably journaled and the driver provides read/write access only with the journal disabled.)

---

