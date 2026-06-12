---
title: "Mounted filesystems limit?"
date: 2006-03-19
forum: Hardware &amp; Laptops
---

### Post by z-vet on 2006-03-19
Hi all. 
How many filesystems can be mounted at once? Is there a limit for this set in Ubuntu/Kubuntu or Linux in general? If the limit exists, how can i change it?
Thanks.

---

### Post by mmcmonster on 2006-03-19
According to [http://nfs.sourceforge.net/](http://nfs.sourceforge.net/) , before the Linux 2.6 kernel, the number of mounted filesystems was limited to (about) 255.  With a google search, I can't seem to find the limit in the Linux 2.6 kernel.

Since every version of Ubuntu is based on the Linux 2.6 kernel, my guess is that you should be able mount 250 drives comfortably.  If you need to mount more than that, there are automounter programs that you can run that will automatically mount filesystems as needed and unmount filesystems that have not been used recently.

Unless you are proficient with Linux kernel source code hacking, it is unlikely that you can change these limits on your own.

---

### Post by z-vet on 2006-03-20
Thank you. :)

---

