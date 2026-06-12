---
title: "Clean Dual w/ Boot Grub Error 15"
date: 2009-03-04
forum: Installation &amp; Upgrades
---

### Post by frcsupport on 2009-03-04
New build, Giga-Byte AM3 ATX board

80GB sda - Vista Ultimate x64
500GB sdb - Data
750GB sdc - Ubuntu Interpid AMD64

I installed Vista first than Intrepid, after the Intrepid install, all I get on boot is Grub Error 15.  I have read through a few posts, and have changed the UUID to root (hd2,0) by booting off of the Live CD, as well as several other solutions, nothing worked.  That brick wall is really starting to hurt my head.  Any help would be greatly appreciated.

I'm at home right now, about to head to the office, so it will be a good hour before I get to check for replies to this thread.  In case anyone wonders why I may not reply back as quickly.

Thanks in advance.

Terry

---

### Post by frcsupport on 2009-03-04
Ok, I'm at the office, can someone please point me in the right direction on this.  We actually have a fair Linux background, Red Hat, Fedora, Mandrake (Mandriva), OpenSUSE.  We are seriousley looking at Ubuntu as our new standard distro, but I can't even evaluate it, if I can't get rid of error 15, and I've already tried all the old standards, that I'm aware of.

Thanks again,

Terry

---

### Post by Elfy on 2009-03-04
Can you boot the livecd and then

```
sudo mkdir /mnt/tmp
sudo mount -t ext3 /dev/sdc1 /mnt/tmp
cat /mnt/tmp/boot/grub/menu.lst
blkid
ls /mnt/tmp/boot
```

If blkid gives noresult

```
ls -al /dev/disk/by-uuid/
```

---

### Post by frcsupport on 2009-03-05
Thank you for the reply.  This system is for my desktop, and I needed to get it up asap, so I removed the 80GB, set the 750GB as sda, and installed both OS's on it, which Grub handled without issue.

I would have preferred the previous setup and will recreate and try your solution on another machine.

Thanks again, and I'll post the results in this thread when I get a chance to try it.

Terry

---

