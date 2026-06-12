---
title: "Cant mount multiple NTFS partition after wubi install"
date: 2008-11-17
forum: Hardware
---

### Post by tropnevad on 2008-11-17
Hello all, I am a new ubuntu user, and i have managed to work out how to mount an NTFs partition, but there is a problem

I have a 100GB harddrive that is split into about 2 50GP partitions (both formatted NTFS), i have vista installed on the first, and then i used the wubi installer to intall ubuntu on part of the 2nd partition. I can mount the first 50GP partition fine in ubuntu using the NTFS-config tool, but am having diffuclties mounting and finding the 2nd NTFS partition.

---

### Post by nickcannard on 2008-11-17
The partition that hosts Wubi will only be accessible from the path "Filesystem/host/"

Meaning: select Places-> Computer and open the drive "Filesystem" 
and the folder "host" 

This is where your missing partition resides. 

I don't believe that you can mount it. You can try using "NTFS configuration tool" to mount it in /media (where all the drive mount points are made)

When NTFS config tool asks for the mount point, you must type only the desired name, NOT /media/desiredname/  that will produce an error. as it is already going to mount it in /media

To install NTFS configuration tool:
open Add/remove applications, and select  Show: "all available applications"
type "ntfs configuration tool"

---

### Post by tropnevad on 2008-11-18
thanks very much :D, managed to find all my data :D

---

