---
title: "cdrom does not mount properly in 10.04"
date: 2010-06-23
forum: Hardware
---

### Post by Azazel on 2010-06-23
ever since i upgraded to Kubuntu 10.04 the ONLY way to mount a cd or dvd is to use the Device Notifier widget. Dolphin will detect that there is a CD and will also detect the title of the CD but will not show its contents. The drive will not be listed in the mtab unless i access it with the device notifier first. I added a line to my fstab for the drive and now i can manually mount it

in the terminal if i do
```
sudo mount /dev/sr0 /media/cdrom
```
then i can access the file with dolphin

I need to at least be able to mount the drive as a user, not as root. It also be nice if the drive automounted when media is attached, as it is supposed to.

Any advice?

---

### Post by Azazel on 2010-06-28
could this have something to do with the new kernel option that makes /dev a tempfs?

---

### Post by phasegen on 2010-08-18
I am having the same problem with a kodak digital camera. lsusb shows the camera, but it's not visible with dolphin, or konqueror. I tried a memory stick on the same usb port, and it works. My phone, normally visible under ubuntu like my camera, isn't in kubuntu either.

---

