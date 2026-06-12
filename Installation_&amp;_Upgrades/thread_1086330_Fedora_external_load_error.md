---
title: "Fedora external load error"
date: 2009-03-03
forum: Installation &amp; Upgrades
---

### Post by wenren on 2009-03-03
So, here's the problem. On my current laptop, a Sony model VGN-FZ283BN, I have two primary partitions. One is my commonly used OS, Ubuntu, and the other is the pre-installed Windows, which I occasionally use for cross-platforming programs and applications that can't run on Linux.

I also have a 1TB Western Digital external hard drive. It runs on USb at typical write speeds of 9MB. I am new to Linux, so before I decide to stick with standard Ubuntu, I want to use this for testing other distributions. The first alternate distribution I tried was Kubuntu, for the KDE. It was actually quite good and reliable, until only one week after installation, when for some reason it failed to boot. Thus, I repartitioned two of the three partitions on the drive, making 3 new portions of 257.1 GB each.

However, one old partition still remains, where I backed up my Windows files until that OS crashed, leading to my initial switch to Linux. I now face a problem. On the second partition, I wanted to install Fedora 10. The installation went fine, although the booting will still not work. I get the same message as I did with Kubuntu. Something was not fixed with the more recent partitioning and installation, leading me to believe that GRUB might be installed on the first partition. Included is a GParted diagram of the disk's partitions. Fedora is installed on the partition that is second from the left.

So, my question is, how will I fix the GRUB loader? Every time I boot with the external hard drive, the GRUB loader fails. I believe that I'll need to use the separate, on-computer Ubuntu to fix it, unless I can fix the problem from within GRUB itself. Do you have any advice?

Edit: It tells me it has an "error 22"

---

### Post by wenren on 2009-03-03
Edit: File didn't work, re-uploading:

---

### Post by wenren on 2009-03-05
Alright...never mind! I reinstalled Fedora, and I discovered that the GRUB had accidentally installed to a single partition's booting mechanism, rather than the MBR itself. Unfortunately, the new installation accidentally erased GRUB on my computer, so in a twisted turn of events, I am now actually running from the external drive's Fedora and I hope to get the Ubuntu drive up and running again soon... I'm presently re-downloading the 8.10 Ubuntu DVD, so that I can install (hopefully) a new GRUB loader.

---

