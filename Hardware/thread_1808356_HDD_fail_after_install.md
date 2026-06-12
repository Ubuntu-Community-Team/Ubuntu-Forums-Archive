---
title: "HDD fail after install"
date: 2011-07-20
forum: Hardware
---

### Post by editheraven on 2011-07-20
Hi. I installed ubuntu yesterday on my WD 200gb sata. I had a ntfs partition wich i deleted and created 3 partitions : one swap and 2 ext4 (/ and /home). After the installation and restart the hdd wich i installed ubuntu on freezed at POST bios detection. It didn't wanted to work either way (the other sata hdd works fine). So i went with my hdd to a hardware store where they also can give maintenance. On their system the hdd was recognised so i deleted the linux partitions and creaded a new ntfs one. Back home, the bios could use the hdd and it works fine. But i'm afraid to install ubuntu again : what if it's gonna give the same problem.

note : i installed the bootloader on / (root).

---

### Post by westie457 on 2011-07-20
> **editheraven said:**
> Hi. I installed ubuntu yesterday on my WD 200gb sata. I had a ntfs partition wich i deleted and created 3 partitions : one swap and 2 ext4 (/ and /home). After the installation and restart the hdd wich i installed ubuntu on freezed at POST bios detection. It didn't wanted to work either way (the other sata hdd works fine). So i went with my hdd to a hardware store where they also can give maintenance. On their system the hdd was recognised so i deleted the linux partitions and creaded a new ntfs one. Back home, the bios could use the hdd and it works fine. But i'm afraid to install ubuntu again : what if it's gonna give the same problem.

note : i installed the bootloader on / (root).

Hello.
In the past I have installed Ubuntu to an external hard drive and a second internal hard drive. In both cases I allowed Grub to use its default settings and had no problems with booting.

Suggest you try a reinstall and let Grub do what it thinks is best.

---

### Post by editheraven on 2011-07-20
I know it's a wise thing to do, but i always insalled grub, or any bootloader, on root and i never had this problem. I'm not sure what really caused this so i'm a little afraid to install again. (now i'm writing from some debian derrivate live distro). I thaught that someone had this problem also. (or it's maybe because the file system? I should install on ext3 ?)

---

### Post by editheraven on 2011-07-20
Ok. I reinstalled ubuntu with grub on MBR (default setting) and it's happening again. The good news is that i can acces my hard by setting in bios lba/large support to disabled. When grub tries to load it says out of space or out of drive.... i can't really remember right now. Now i can't understand why it says that and why my hdd is only recognised with lba disabled. It's, obviously, a problem with grub. So : can i install lilo bootloader, by default, when installing ubuntu?

---

