---
title: "Acer Aspire One 722 can't find root device"
date: 2011-07-22
forum: Hardware
---

### Post by yelvington on 2011-07-22
Trying to install Natty on an AO722. 

Following instructions found on this forum, I set the BIOS to attempt a network boot, so I'm beyond that problem. I can boot from a thumb drive, connect to the Internet via wi-fi, and run the installer. I partitioned the disk, shrinking the Windows 7 partition. The installation proceeded normally.

However, after the installation, I'm  not able to boot into Linux. I get as far as a blank auburn screen, then the system hangs.

Booting into recovery mode results in the system proceeding to the point of attempting to mount the root partition and failing because the disk doesn't exist (it prints out the very long UID). It drops into Busybox.

---

### Post by yelvington on 2011-07-22
Attempting to fix this, I booted from the USB drive, did a chroot to the hard disk, ran apt-get upgrade. Everything other than the kernel succeeded. 

Edited /etc/default/grub and uncommented GRUB_DISABLE_LINUX_UUID=true
regenerated grub.cfg

No luck; now it merely fails with "/dev/sda6 does not exist."

/dev/sda6 is the correct partition.

---

### Post by yelvington on 2011-07-22
Fixed. Apparently the installation process attempted to update the kernel but failed while making Grub believe it had succeeded. Doing chroot from the usb to the hard disk, then running apt-get install linux-generic and the headers, made the kernel whole again, and the laptop is up and running.

Others have reported issues with the video driver, but I am not seeing any. 

Natty is considerably snappier than Windows 7.

I have not benchmarked this against my Acer 1410, an older but very similar model with a dual-core Centrino.

---

