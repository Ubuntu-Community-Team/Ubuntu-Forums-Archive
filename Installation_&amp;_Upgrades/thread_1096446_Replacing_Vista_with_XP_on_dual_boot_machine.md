---
title: "Replacing Vista with XP on dual boot machine"
date: 2009-03-14
forum: Installation &amp; Upgrades
---

### Post by O-pos on 2009-03-14
Hello,

I have a dual boot system on my machine, Ubuntu and Windows Vista. Vista drives me nuts, would like to remove it and install Windows xp. The only thing which is holding me is that I am afraid not to damage fine structure of other partitions used by linux, as well as GRUB, which could be changed/altered in a way that linux would not boot.

Any suggestions what would be the easiest cleanest way to get rid of Vista and install windows XP?

Thanks, O-pos

---

### Post by mikewhatever on 2009-03-14
There is no way to preserve GRUB when installing Windows. The good news is, it can be reinstalled either from the live cd or supergrub disk.
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

### Post by O-pos on 2009-03-14
Thanks. Besides Grub issue, what else do I need to consider while installing XP? do I have format Vista partition first as NTFS or unallocated? How would windows XP be re-mounted in Linux?

---

### Post by mikewhatever on 2009-03-15
> **O-pos said:**
> Thanks. Besides Grub issue, what else do I need to consider while installing XP? do I have format Vista partition first as NTFS or unallocated? How would windows XP be re-mounted in Linux?

Windows XP usually wants NTFS, and it should be mounted as another NTFS partition.

---

