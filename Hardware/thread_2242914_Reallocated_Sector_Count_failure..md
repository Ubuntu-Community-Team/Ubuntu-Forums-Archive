---
title: "Reallocated Sector Count failure."
date: 2014-09-04
forum: Hardware
---

### Post by elianmanzueta200 on 2014-09-04
I was going to install Windows 7 on a USB so I could use some other programs, so I attempted to format the drive with DISKPART. It took about an hour to format it into NTFS, and then it failed. I tried again and it said there was no disk. So I booted into my Ubuntu 14.04 USB and tried to re-install it, but it said that on the drive was likely to fail soon so I looked at S.M.A.R.T after some searching, and it said the reallocated sector count failed. I'm pretty sure it's that failed Windows 7 install, but I've done this before with no problem, with GPart though, but it wasn't working. Anyone know any solutions? Everything I searched said to replace the drive, but I don't think I can do that..

Help?

---

### Post by sandyd on 2014-09-04
> **elianmanzueta200 said:**
> I was going to install Windows 7 on a USB so I could use some other programs, so I attempted to format the drive with DISKPART. It took about an hour to format it into NTFS, and then it failed. I tried again and it said there was no disk. So I booted into my Ubuntu 14.04 USB and tried to re-install it, but it said that on the drive was likely to fail soon so I looked at S.M.A.R.T after some searching, and it said the reallocated sector count failed. I'm pretty sure it's that failed Windows 7 install, but I've done this before with no problem, with GPart though, but it wasn't working. Anyone know any solutions? Everything I searched said to replace the drive, but I don't think I can do that..

Help?

If the reallocated sector count is increasing with each boot/disk access, it is an indication of disk problems, and you probably should _not_ use that disk.

Also, how did you perform the test?
Should be something like (assuming disk is /dev/sda)
```

sudo apt-get install smartmontools
sudo smartctl -t long /dev/sda
```

---

### Post by elianmanzueta200 on 2014-09-05
> **sandyd said:**
> If the reallocated sector count is increasing with each boot/disk access, it is an indication of disk problems, and you probably should _not_ use that disk.

Also, how did you perform the test?
Should be something like (assuming disk is /dev/sda)
```

sudo apt-get install smartmontools
sudo smartctl -t long /dev/sda
```

Well, I just opened up disks and it said it was likely to fail soon, so I just ran another test. I'll try again right now.

Picture: [http://i.imgur.com/bQZkSC5.png](http://i.imgur.com/bQZkSC5.png), whenever I try to do a SMART test it has this error:

sk_disk_smart_self_test: Operation not supported (udisks-error-quark, 0)

EDIT:

Whenever I try to install Ubuntu 14.04, it crashes and says something about my CD/DVD player. Maybe I have to re-install Ubuntu on my USB? I'm not installing it on a DVD/CD, I am using USB.

---

### Post by weatherman2 on 2014-09-05
Your hard drive is clearly failing.  Replace it.

---

### Post by elianmanzueta200 on 2014-09-06
Uhh, I just checked again and it actually is decreasing. It used to have about 19K sectors and now it has 16K sectors. I don't know if that's good or not, but at least it's not increasing, right?

EDIT:

Installer Error: 

The installer encountered an error copying files to the hard disk:

[Errno 5] Input/output error: '/target/usr/src/linux-headers-3.13.0-32'

This is often due to a faulty hard disk. It may help to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.

---

### Post by elianmanzueta200 on 2014-09-14
Fixed by enabling LVM.

---

