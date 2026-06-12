---
title: "hardware raid + LVM"
date: 2014-11-02
forum: Hardware
---

### Post by jhayes on 2014-11-02
So some reading has indicated that putting /boot, /, and maybe /swap-space all inside LVM partitions ( causes problems booting?). So here is my setup, I have a supermicro server with 12 hot-swap hard drives in it. Have 2 beefy hardware raid cards, with 6 drives in raid 50 on each card . ( cant spend $, use what we have etc.). I assume that if I booted with a live cd, and it loads the drives, a fdisk -l would show 2 "drives, /dev/sda, /dev/sdb. Was thinking, carve out some space from the front of each, maybe 4-8gb, for /boot, / , and /swap. and use the rest of the space on both for a LVM group, to present as one big mount point through NFS.  I think as long as I carve out exactly the same amount of space from each, leaving 2 same sized partitions for the LVM's it might work? can't boot from a flash-drive, can't boot from a 13th drive. have to use the hardware raid cards ( not enough ports on the mobo), and don't think allowed to just do a full on software raid. 

have instructions here how to most of this: [https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
suggestion's on if this will work, recommended, better way?

---

