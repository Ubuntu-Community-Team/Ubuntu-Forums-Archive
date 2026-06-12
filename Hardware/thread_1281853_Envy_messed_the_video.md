---
title: "Envy messed the video"
date: 2009-10-03
forum: Hardware
---

### Post by DMurray on 2009-10-03
Hi all.
The scenario is: I`m trying to use the kernel 2.6.24-24, but I can`t have my video card (nvidia 9600gt) working on this thing.
I could successfully use envy to install the module for 2.6.24-23, but it didn`t work this time. When I ran "envyng -t" with the 24-24 loaded, and asked a manual install (automatic didn`t work), it downloaded a bunch packages and version 173 of the nvidia driver!
I was using version 185 since february in 24-23, and how come it downloaded version 173 for a later kernel?
Ok... it installed, didn`t get my X to load, and when I chose 24-23 (which worked), it also installed version 173 for it! I checked in lib/modules that my nvidia.ko was in fact the old one, but now modprobe was looking for it in dkms/updates, and no longer in kernel/drivers/video/nvidia. I made a symlink to solve it, and the module loads, but X refuses to load.
Damn retarded programs... I`m wondering why things worked in the past and get worse when they should evolve...

---

### Post by markbuntu on 2009-10-05
Envy has never worked for me. it always tries to misinstall old drivers.

---

