---
title: "Add / remove / replace sata HD question"
date: 2019-12-22
forum: Hardware
---

### Post by ra7411 on 2019-12-22
Whenever I add or remove or replace a non o/s sata HD in a desktop, I wind up having a grub problem on bootup and have  to boot the install disk, try ubuntu, and do a grub repair in a terminal.

Is there a way of avoiding this without using a usb dock for the HD (too slow data transfer rates) ?

Thanks

---

### Post by yancek on 2019-12-22
Is this an MBR/Legacy install or UEFI?  With a Legacy install, you should have the disk with the operating system on it set to first boot priority.  If that is the case, I don't see how you could have a boot problem.  Ubuntu 18.04 being the only OS you have according to your post.  Similar for an EFI install unless you have the EFI partition on the wrong disk?  If you don't have this resolved, you might go to the boot repair site and use the Create BootInfo Summary option to gather information.  When it finishes running, you will get a link which you can post here if you can't resolve it on your own.  Also, best to use the ppa described under 2nd option on that page. 

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by ra7411 on 2019-12-22
> **yancek said:**
> Is this an MBR/Legacy install or UEFI?  With a Legacy install, you should have the disk with the operating system on it set to first boot priority.  If that is the case, I don't see how you could have a boot problem.  Ubuntu 18.04 being the only OS you have according to your post.  Similar for an EFI install unless you have the EFI partition on the wrong disk?  If you don't have this resolved, you might go to the boot repair site and use the Create BootInfo Summary option to gather information.  When it finishes running, you will get a link which you can post here if you can't resolve it on your own.  Also, best to use the ppa described under 2nd option on that page. 

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

It's a bios machine, sdc1 is 1804, sdb1 is 1804, and when I power off and switch sata cables to a get a sda for data backup I often (not always as i previously implied) get a grub problem and have to fix it.

---

### Post by TheFu on 2019-12-22
If you are changing SATA connections around, expect boot issues.  The BIOS expects to boot using the same SATA port. Depending on where the boot MBR records are located, you may be moving it and the BIOS has no idea where to look.

If you don't want boot issues, don't move SATA connections around.

---

