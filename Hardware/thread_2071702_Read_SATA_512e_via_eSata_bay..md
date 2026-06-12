---
title: "Read SATA 512e via eSata bay."
date: 2012-10-16
forum: Hardware
---

### Post by netJackDaw on 2012-10-16
Hi!

I have a problem when I try to read data from a SATA 512e disk mounted in an eSATA bay. When the 512e disk is mounted in the computer (laptop) it works fine to read and write. I have Ubuntu 12.04 installed on it (upgraded factory install from Dell).

I have switched drives so that I now have an SSD with 12.04 in my laptop. When I mount the old 512e disk via eSATA and try to read data from it with my new system I get problems. Some folders that are not empty seem empty when looking into them. Some folders have question marks that indicates that the files cannot be read. ...and so on. I get permission warnings when trying to copy.

My questions are:

Is something missing here? Is the driver/support for 512e installed by default in a new system? How do I activate it?

Does the external eSATA bay have to have some special features to be able to read 512e disks?

I have the data from my 512e already copied elsewhere so my data is safe. I just want to know how it works and also be able so make use of the 512e disk.

/A

---

### Post by netJackDaw on 2012-10-16
Just realized that this is not an issue of SATA, eSATA or 512e at all. Its all about permissions. The user that created the files cannot read them from another installation as he do not own them. So the solution is to take ownership of the files and folders or use an account with root privileges to read them.

I think that this behavior was different under 10.04 with a externally mounted disk. I've rescued data many times this way before... Maybe someone can shed light on that! ...after you had a good laugh.

---

