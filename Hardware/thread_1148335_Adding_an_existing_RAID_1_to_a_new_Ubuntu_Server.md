---
title: "Adding an existing RAID 1 to a new Ubuntu Server?"
date: 2009-05-04
forum: Hardware
---

### Post by lightnb on 2009-05-04
Our small business has been using "SME Server 7" as our file server for several years now. We would like to change our server's OS to Ubuntu, but would need to do it without loosing the critical data on the array.

The current set-up has 3 hard drives:
The first holds the root partition, and the file system.
The other two drives are members of a RAID 1 array, and hold all of the shared files (for our employees).

The SME Server installer created the array automatically during the install, so I don't know which variety of array it created.

What is the best way to:

1. Determine if the existing RAID array is compatible with Ubuntu?
2. Proceed with the installation so the old RAID array will work with the new system, but not be overwritten in the process?

---

