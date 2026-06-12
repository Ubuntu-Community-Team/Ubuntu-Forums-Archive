---
title: "ext3 external hard drive on Windows 7"
date: 2009-12-05
forum: Hardware
---

### Post by lorstan on 2009-12-05
I have both an Ubuntu machine and a Windows machine and for reasons related to this sometimes want to read an ext3 external hard drive on the Windows machine. Under Windows XP, I used ext2fsd to enable this. This has been a problem since upgrading the Windows machine to Windows 7 due to problems with ext2fsd/ext2ifs (though I see things are happening with ext2fsd).

I thought I would post my particular solution, which seems to be working for me so far. I have installed WMware Player 3 (which is freeware) on the Windows 7 machine and set up an Ubuntu VM. This allows me to plug in the ext3 external USB hard drive and use it from the Ubuntu VM. I can then also simply copy the files from the Ubuntu VM and then paste them into the Windows file system. It is not necessary to copy to Ubutu first and then Windows - I can copy straight from the external hard drive to Windows.

I have tested this with ext3 with large partitions and files (biggest file copied so far was 4.7 GB). All has been OK so far. I have not yet tried this with ext4 but this also may work.

This solution suits me as it is easy enough to use, avoids dual booting and associated restarts. Also the Ubuntu VM is useful to me for other reasons. This won't be a solution for most people but might help some.

Incidentally, I also tried Virtual Box. This is nice software (shared folders worked better for me, for example) but unlike VMware, devices used by its VMs need to be recognisable by the host OS, which was a show stopper for me.

---

