---
title: "Mounting/using partition?"
date: 2007-11-05
forum: Hardware &amp; Laptops
---

### Post by Iamshiznaki on 2007-11-05
I  recently had a lot of trouble getting my laptop working with 7.10, I was pretty stupid diving in without knowledge of partitions, etc. But anyway, on to the issue.

I wiped the hard drive, started from scratch. I set up ubuntu to be the my only OS, and set it to have a 15g partition for the filesystem. I also set up 500 mb for the swap, leaving about 40g I hoped to use for storage, etc. I don't have the option to mount it so I used gparted to attempt to format it in a way that I could use it for storage. It worked, I was able to mount the drive and give myself permissions over it, but upon restart the system failed to boot after the grub screen. I used recovery mode to find the problem, it told me that "file system check failed" Apparently, if I use the storage partition, it aquires the wrong UUID, and the system fails to boot. When I fixed the problem, I could no longer mount the drive.

What I'm asking is, is there a way I can use the 40g partition, and still have all my UUID's correct so the system will boot?

---

### Post by ROBarber on 2007-11-05
here you can find a solution to mount the free space to /home.
[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

good luck

---

