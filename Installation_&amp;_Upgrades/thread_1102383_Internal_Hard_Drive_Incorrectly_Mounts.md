---
title: "Internal Hard Drive Incorrectly Mounts"
date: 2009-03-21
forum: Installation &amp; Upgrades
---

### Post by wenren on 2009-03-21
Alright. So, here's the problem:


I installed a variety of operating systems on my computer. I have two drives, one internal and one external. On the internal, there is a Windows Vista recovery partition, a Windows 7 Beta partition, and my ubuntu partition. On my external drive, I have 4 primary partitions. One is a general file backup partition, another is for Fedora, and the 4th is presently empty. I chose to install CentOS on the 3rd partition, and I included a swap partition.

After the installation, I realized that my computer was, for the most part, disfunctional. The CentOS grub loader doesn't load any of the other OSes, for a reason I failed to identify, and I now really need to reinstall the ubuntu grub. However, here is the catch.

The CentOS completely disrupted the partitions. Now, I have booted my Ubuntu Live DVD, and I would like to perform the fix. Despite my efforts at trying every conventional tctic for reinstallation, nothing has worked. Recently, however, I discovered the cause: my Ubuntu DVD seems to think that the internal hard drive is removable media, and has assigned its partitions to the 'media' folder instead of the 'dev' folder.

Is there any way to reset this?

---

### Post by wenren on 2009-03-21
Nevermind, I was able to get it to work!

---

