---
title: "Mounting USB drives at bootup"
date: 2005-11-01
forum: Hardware &amp; Laptops
---

### Post by 5horizons on 2005-11-01
Hello,

I have a couple Kubuntu machines that I have to take care of.  USB mass storage devices (using fat32 partitions) work fine if I plug them in while the computer is up and running, they are mounted as /media/[NameOfDevice].  I have no problem reading/writing to them.

However, if the computer is rebooted these USB devices are not mounted.  Is there a way to have these devices automatically mounted at bootup (didn't hoary do this?)?

Thanks,
Chris

---

### Post by 5horizons on 2005-11-01
I forgot to mention that I've tried adding entries in /etc/fstab that correspond to these devices, such as the following:

/dev/sdf1       /mnt/usb1      vfat    defaults,rw,users,umask=000  0       0

Even If I add the "auto" option it still doesn't mount at while booting.  I'm quite sure this entry is correct, because I can mount and unmount the USB drive without an issue - it just doesn't want to mount at bootup.

Chris

---

