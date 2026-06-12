---
title: "how to change HDD to SSD"
date: 2013-09-09
forum: Hardware
---

### Post by cisco2 on 2013-09-09
Hi

I want to change my HDD for Sandisk SSD, but I want to move my system to the new ssd.
I'm using UBUNTU 13.4 and I don't know what program use.

What program do you recommended?
IF the Sandisk work right with ubuntu 13.4?

Thankx

---

### Post by varunendra on 2013-09-09
Welcome to the forums cisco2 !

What matters is the interface and file-system, and both would be same for both the HDD and the SSD.

Use **GParted** from Ubuntu live CD/USB to create partitions on the SSD. Keep the system partition (to which you would be moving the current installation) equal or larger than the current one. Then download **[Clonezilla]("http://clonezilla.org/")** live cd iso > burn it to a cd and use it to clone your system partition to the SSD.

**EDIT:**
Clonezilla Tutorial with screenshots : [http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)

---

