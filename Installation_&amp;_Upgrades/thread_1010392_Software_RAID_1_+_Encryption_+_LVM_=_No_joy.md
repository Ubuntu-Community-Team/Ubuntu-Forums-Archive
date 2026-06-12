---
title: "Software RAID 1 + Encryption + LVM = No joy"
date: 2008-12-13
forum: Installation &amp; Upgrades
---

### Post by Tonohono on 2008-12-13
Right.
I've successfully installed with an encrypted LVM.
I've successfully installed with a software RAID 1 and LVM.
But an software RAID 1 and encrypted LVM? Not so much.

When attempting the last method, I first configure software RAID 1, then the encrypted partition, and finally the LVM. Installation of Ubuntu and GRUB proceeds without incident. However, upon booting I'm dropped into BusyBox.

Pictures are neat, so I hope they help.

**Software RAID 1 + Encryption + LVM** partition scheme. I combine the methods I've used in the paste to create encrypted LVMs and software RAID 1 LVMs. For some reason which thus far eludes me, this doesn't work.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=96285&stc=1&d=1229215613[/IMG]

**The error received during boot.**
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=96279&stc=1&d=1229208835[/IMG]

I appreciate any help provided~

---

