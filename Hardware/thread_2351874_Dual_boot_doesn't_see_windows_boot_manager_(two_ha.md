---
title: "Dual boot doesn't see windows boot manager (two hard drives)"
date: 2017-02-07
forum: Hardware
---

### Post by mar0029 on 2017-02-07
Hello!

The system I'm working on has two hard drives. A 1TB drive and a 250GB SSD drive. [Image of partitions from Window Disk Management]("http://imgur.com/a/wlEi2").
BIOS sees both boot options but GRUB does not. I want GRUB to be able to see both the Windows and the Ubuntu boot options.

Thank you for your time!

---

### Post by oldfred on 2017-02-07
First try this:
sudo update-grub

But if Windows is really BIOS and Ubuntu UEFI it will not work as UEFI & BIOS are not compatible.
While you do show an ESP - efi system partition on sda, you do not have the normal Windows partitions for UEFI boot.
Once you start booting in one mode from UEFI boot menu, you cannot switch, or once to grub menu you can only boot systems installed in same boot mode as Ubuntu & grub.

       May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 


 BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions)

---

