---
title: "Hard Drive booting error"
date: 2009-07-02
forum: Hardware
---

### Post by winrowc on 2009-07-02
I have an 80 gb ide hard drive with jaunty and a 1tb sata hard drive with Windows 7. The Sata drive works fine, but my new Gigabyte ep45-ud3r motherboard simply will not boot with the ubuntu hard drive anymore. I have unplugged the Windows drive and set the ubuntu drive as master/single with the jumpers but it isn't recognized as far as I can tell in the Bios. I then put it as slave with the sata drive, and using the partition tool in Windows 7 I can see the drive, so all the cables are at least connected, but I can't edit it or explore it because its a different file system.

I think the cause of this problem may be that I turned the machine off midway through loading  ubuntu from a hibernation. When I turned it back on again, it said something about an error and was trying to recover a disk image or something from a hibernation, so after about 5 minutes of waiting I turned it off again, figuring I would make it start fresh. When I came back to wanting to use the ubuntu drive, its now not loading GRUB nor booting. I know that it can work so its not like the drive isn't compatible or something I just need to figure out why the computer won't even load GRUB. Any suggestions?

---

### Post by tvtech on 2009-07-02
boot a live cd and see if you can mount the hard drive.

---

