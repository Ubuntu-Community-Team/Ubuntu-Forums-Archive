---
title: "HP dm1z-3000 disk freezing with kernel 2.6.38"
date: 2011-03-28
forum: Hardware
---

### Post by adamis on 2011-03-28
I just got my HP dm1z a few days ago. I also purchased a Seagate Momentus XT hybrid ssd (It has 4gb of NAND for caching and 500gb on normal platters).

I loaded a daily spin of pre-release Kubuntu 11.04 on it that contains the 2.6.38-generic-7 kernel on it. The laptop has been very fast and responsive, but I have noticed that any sort of file transfer involving large files or lots of files will result in a complete hard lock. It took me two days to figure this out, I was trying to restore my home directory from a backup and it kept locking up. I tried everything from using a USB drive to copy, as well as trying to copy over the network. 

I ended up installing a 2.6.35 kernel to complete my system restore and it copied without any problems. Oddly enough, as long as I don't copy large amounts of files anywhere, I can use the 2.6.38 kernel for day to day work without issues.

Having narrowed this down to an issue with the 2.6.38 kernel, I am looking to see if anyone else has experienced this sort of problem on their dm1z, or if it is unique to the hp dm1z and the after market Momentus XT disk.

---

### Post by nefan on 2011-05-01
I got exactly the same problem without the Seagate disk. Will try the older kernel as you suggest. Are you aware if a bug report has been filed?

---

