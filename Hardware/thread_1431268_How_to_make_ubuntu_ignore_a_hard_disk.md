---
title: "How to make ubuntu ignore a hard disk?"
date: 2010-03-16
forum: Hardware
---

### Post by sideral on 2010-03-16
One of my two hard drives apparently has bad sectors, which makes ubuntu show a lot of warnings while booting, and to last more than 2 minutes on the boot screen. This disk is a ntfs windows drive which I don't care if ubuntu can't read . I just want Ubuntu to ignore it. I edited /etc/fstab adding the noauto option, but it didn't work.. I'm clueless .. Is there another way? Please help me!

---

### Post by Ayuthia on 2010-03-16
Have you tried commenting out that line in fstab?

---

### Post by sideral on 2010-03-16
Yes, commenting it out was the first thing I tried, but I wasn't successful, so I learned a bit about fstab and tried with noauto. 

I know the problem comes from this drive because 1 in every 5 times, ubuntu doesn't show the warnings and boots in seconds. When this happens, the drive appears on the list of devices available for mounting. On the other hand, when the warnings show up, the drive doesn't appear on this list, which means, I guess, that ubuntu tried to read it.

---

